Nikolay Smirnov
============
* Email:                            n.smirnov.kz@gmail.com
* Phone:                            +77052795170
* telegram                          smi_nik

Summary
----------
Hello. My name is Nikolay. I work as a leading programmer in a great company.
I very like my profession

**My main goals:**

* Become a senior programmer

* Learn english

* Learn new approaches in developing


Skills
--------------------
**Programming Languages and frameworks:**
* Javascript
* HTML
* CSS
* PHP
* YII 2.0
* VueJS
* Or3
* Alfresco

Code example
----------------------------------------
```javascript
  /*
    данный код создает запись продления контрольного срока исполнения документа.
    Возможность продления предоставляется всем пользователям с ролью Делопроизводитель
    из Архив документов - кнопка Продлить.
    Результат: создание записи продления, изменение даты контрольного срока в карточке документа,
      увеличение счетчика количества продлений для отчета.
  */

  <import resource="classpath:alfresco/extension/templates/webscripts/ru/mrgrechkinn/core/workflow/mgCoreRegistryEventHandlers.js">

  var runtimeService = function() {
    var ctx = Packages.org.springframework.web.context.ContextLoader.getCurrentWebApplicationContext(); 
    return ctx.getBean(org.activiti.engine.impl.RuntimeServiceImpl);
  }();
  var ctx = Packages.org.springframework.web.context.ContextLoader.getCurrentWebApplicationContext();
  var sR = ctx.getBean(Packages.org.alfresco.repo.service.ServiceDescriptorRegistry);

  function main() {
    if (json) {
      var wfId = json.get("wfId");
      var extendDate = json.get("extendDate");
      var extendDoc = json.get("extendDoc");
      var extendComment = json.get("extendComment");

      var registryObject = runtimeService.getVariable(wfId, "registryObject");

      //создаем объект продления
      java.lang.System.out.println(asdadasdqwesa);
      var prodObject = createProdlRecord(extendComment, extendDate, stringToArray(extendDoc, ","));
      //связываем его с объетом
      registryObject.createAssociation(prodObject, "mgc:prodlenieRecord");
      prodObject.properties["mgc:prodlIsExtended"] = true;
      prodObject.properties["mgc:prodlDateOld"] = runtimeService.getVariable(wfId, "dueDate");
      prodObject.save();
      //в объект
      registryObject.properties["mgc:dueDate"] = extendDate;
      registryObject.save();

      var valueDate = new Date();
      valueDate.setTime(extendDate);
      runtimeService.setVariable(wfId, "mgc_dueDate", new java.util.Date(valueDate.getTime()));
      runtimeService.setVariable(wfId, "extendDate", new java.util.Date(valueDate.getTime()));

      //счетчик продлений для отчета (выгрузки)
      // в новой версии можно будет просто сделать count записей продления
      var prodCount = runtimeService.getVariable(wfId, "prodCount");
      if (prodCount === null || prodCount === undefined) {
        prodCount = 0;
      } else {
        prodCount = prodCount + 1;
      }
      runtimeService.setVariableLocal(wfId, "prodCount", prodCount);
    }
  }

  Packages.org.alfresco.repo.security.authentication.AuthenticationUtil.setRunAsUserSystem();
  main();
```

Experience
---------

My list of projects: https://gitlab.com/smi_nik

Education
---------

2008-2012
:   **College of Management**: Astana, Kazakhstan
:   **TUSUR University**: Tomsk, Russia

English
---------

Pre-intermedia
