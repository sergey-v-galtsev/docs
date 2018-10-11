# Метод listAccessBindings
Возвращает список привязок прав доступа к указанному
сервисному аккаунту.
 

 
## HTTP-запрос
`GET /iam/v1/serviceAccounts/{resourceId}:listAccessBindings`
 
## Path-параметры {#path_params}
 
Name | Description
--- | ---
resourceId | Обязательное поле. Идентификатор ресурса, для которого запрашивается список привязок прав доступа.  Чтобы получить идентификатор ресурса, используйте соответствующий запрос List. Например, используйте запрос [list](/docs/resource-manager/api-ref/Cloud/list) для получения идентификатора ресурса Cloud.  Максимальная длина — 50 символов.
 
## Query-параметры {#query_params}
 
Name | Description
--- | ---
pageSize | Максимальное количество результатов на странице ответа на запрос. Если количество результатов больше чем pageSize, сервис вернет значение nextPageToken, которое можно использовать для получения следующей страницы. Допустимые значения от 0 до 1000 включительно. Значение по умолчанию: 100.  Допустимые значения — от 0 до 1000 включительно.
pageToken | Токен страницы. Установите значение pageToken равным значению поля nextPageToken прошлого запроса, чтобы получить следующую страницу результатов.  Максимальная длина — 100 символов.
 
## Ответ {#responses}
**HTTP Code: 200 - OK**


 
Поле | Описание
--- | ---
accessBindings | **object**<br><p>Список привязок прав доступа для указанного ресурса.</p> 
accessBindings.<br>roleId | **string**<br><p>Идентификатор ресурса <a href="/docs/iam/api-ref/Role#representation">Role</a> который назначен для субъекта, указанного в параметре subject.</p> <p>Максимальная длина — 50 символов.</p> 
accessBindings.<br>subject | **object**<br><p>Обязательное поле. Субъект, для которого создается привязка прав доступа. Может представлять собой учетную запись с уникальным идентификатором в облаке или системную группу с общим системным идентификатором.</p> <p>Может содержать один из следующих наборов параметров:</p> <ul> <li><code>type = system, id = allUsers</code>.</li> <li><code>type = system, id = allAuthenticatedUsers</code>.</li> <li><code>type = userAccount, id = &lt;идентификатор пользователя в облаке&gt;</code>.</li> <li><code>type = serviceAccount, id = &lt;идентификатор пользователя в облаке&gt;</code>.</li> </ul> 
accessBindings.<br>subject.<br>id | **string**<br><p>Идентификатор субъекта.</p> <p>Может содержать одно из следующих значений:</p> <ul> <li> <p><code>allUsers</code>: Специальный системный идентификатор, представляющий любого пользователя. Его можно использовать только если в параметре type передано значение <code>system</code>.</p> </li> <li> <p><code>allAuthenticatedUsers</code>: Специальный системный идентификатор, представляющий любого пользователя, прошедшего аутентификацию. Его можно использовать только если в параметре type передано значение <code>system</code>.</p> </li> <li> <p><code>&lt;идентификатор пользователя в облаке&gt;</code>: Идентификатор, представляющий учетную запись пользователя. Его можно использовать только если в параметре type передано одно из следующих значений: <code>userAccount</code> или <code>serviceAccount</code>.</p> </li> </ul> <p>Максимальная длина — 50 символов.</p> 
accessBindings.<br>subject.<br>type | **string**<br><p>Тип субъекта.</p> <p>Может содержать одно из следующих значений:</p> <ul> <li> <p><code>system</code>: Системная группа. Представляет несколько учетных записей с общим системным идентификатором.</p> </li> <li> <p><code>userAccount</code>: Учетная запись пользователя. Дополнительные сведения см. в разделе <a href="/docs/iam/concepts/users/users">Пользователи Яндекс.Облака</a>.</p> </li> <li> <p><code>serviceAccount</code>: Сервисный аккаунт. Дополнительные сведения см. в разделе <a href="/docs/iam/concepts/users/service-accounts">Сервисные аккаунты</a>.</p> </li> </ul> 
nextPageToken | **string**<br><p>Токен для получения следующей страницы результатов в ответе. Если количество результатов больше чем pageSize, используйте nextPageToken в качестве значения параметра pageToken в следующем запросе списка ресурсов. Все последующие запросы будут получать свои значения nextPageToken для перебора страниц результатов.</p> 