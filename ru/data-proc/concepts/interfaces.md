# Работа с сетевыми интерфейсами компонентов

{{ dataproc-name }} позволяет создавать кластеры только с внутренними адресами Яндекс.Облака. Сетевые и веб-интерфейсы компонентов при этом недоступны извне. Для внешней связи с такими компонентами как HDFS NameNode, YARN ResourceManager и другими необходимо маршрутизировать трафик через промежуточную виртуальную машину, для которой выделен публичный IP-адрес.

## Перенаправление портов {#routing}

Чтобы получить доступ к сетевому интерфейсу компонента из интернета, [создайте](../../compute/operations/vm-create/create-linux-vm.md) промежуточную виртуальную машину в сервисе {{compute-full-name}}. Эта ВМ должна иметь публичный IP-адрес и находиться в одной сети с нужным кластером {{ dataproc-name }}.

Чтобы соединиться с нужным портом хоста {{ dataproc-name }}, выполните следующую команду:

```
ssh -A -J <публичный IP-адрес ВМ> -L <номер порта>:<FQDN хоста Data Proc>:<номер порта> root@<FQDN хоста Data Proc>
```

Найти FQDN хоста {{ dataproc-name }} можно на странице кластера {{ dataproc-name }}, на вкладке **Хосты**, в столбце **Имя хоста**.

Номера портов для компонентов {{ dataproc-name }} приведены ниже.

## Компоненты и порты {#port-numbers}

| Сервис | Порт |
| ----- | ----- |
| HDFS Name Node | 9870 |
| YARN Resource Manager | 8088 |
| YARN Application History | 8188 |
| MapReduce Application History | 19888 |
| Hive Server2 | 10002 |
| HBase Master | 16010 |
| HBase REST | 8085 |
| Zeppelin | 8890 |
| Oozie | 11000 |
