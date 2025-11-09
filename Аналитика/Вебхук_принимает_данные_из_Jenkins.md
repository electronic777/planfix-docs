В большой команде, которая работает над общим проектом, иногда важно знать, готово ли к работе новое обновление в проекте. Такое оповещение в виде комментария можно отправлять разработчикам в соответствующую задачу в ПланФиксе именно в тот момент, когда новые доработки готовы к использованию. Такой функционал возможно реализовать, используя [Jenkins](https://www.jenkins.io/) и [входящие вебхуки](../Общие/Входящие_вебхуки.md). 


  


## Как это сделать


  * Сформируйте коммиты такого вида: 123456 - текст коммита, где 123456 - номер задачи в ПланФиксе.

  * Создайте вебхук, который получит коммиты.

  * В [Jenkins Pipeline](https://www.jenkins.io/doc/book/pipeline/) допишите код, который отправит данные на вебхук.


  


## Настройка вебхука


![Bvldiw.png](images/Bvldiw.png)


  


## Код в Jenkins


Две вспомогательные функции: 

    

    

    @NonCPS

    def getTaskNumber(text) {

       def m = (text =~ /\d+/);

       def taskNumber = m ? m[0] : "";

       return taskNumber

    }

    


  


    

    

    @NonCPS

    def getChangesByTaskNumber() {

       def changes = [:]

       def maxMessages = 50;

    

       def changeLogSets = currentBuild.changeSets

    

       for (int i = 0; i < changeLogSets.size(); i++) {

           def entries = changeLogSets[i].items

           for (int j = 0; j < entries.length && i + j < maxMessages; j++) {

               def entry = entries[j]

               def taskNumber = getTaskNumber(entry.msg);

               if(taskNumber != "") {

                   if(!changes.containsKey(taskNumber)) {

                       changes[taskNumber] = "";

                   }

                   changes[taskNumber] += entry.msg + "<br>"

               }

           }

       }

    

       return changes

    }

    


  

Код, который вставляем после завершения всех операций: 

    

    

    def deployedTasks = getChangesByTaskNumber()

    deployedTasks.eachWithIndex { key, value, i -> 

        httpRequest contentType: "APPLICATION_JSON_UTF8", httpMode: "POST", requestBody: "{ \"task\" : ${key}, \"comment\" : \"${value.replaceAll('"','\\\\"')}\", \"project\" : \"project-name\", \"branch\" : \"${env.gitlabBranch}\"}", responseHandle: "NONE", url: "https://myacc.planfix.ru/webhook/json/b7mh-dead-687f-lpwq", consoleLogResponseBody: true

    }

    


  


## Итоговый результат


Разработчик увидит в задаче такой комментарий: 


![DyTZ59.png](images/DyTZ59.png)
