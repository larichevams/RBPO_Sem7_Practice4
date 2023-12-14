**Задание 1**
1. Исходный PHP-код
   ![image](https://github.com/larichevams/RBPO_Sem7_Practice4/assets/71451332/f915ca6a-694d-44d4-8caa-78fc513f2a49)
2. Анализ кода статическим анализатором SonarCloud
   ![image](https://github.com/larichevams/RBPO_Sem7_Practice4/assets/71451332/523980f1-386c-4be0-84c3-95165212586e)
3. Найденная уязвимость в коде
   ![image](https://github.com/larichevams/RBPO_Sem7_Practice4/assets/71451332/6074e8b8-d4d8-4daf-a73e-bacad61228b6)

**Задание 2**

Анализ также был проведен в том числе с использованием статического анализатора SonarCloud
![image](https://github.com/larichevams/RBPO_Sem7_Practice4/assets/71451332/64fc247d-da7d-449d-ac7a-48eef36a5097)
По сути, этот код полностью аналогичен коду из первого задания и содержит ту же самую уязвимость:
CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection'). 
Переменная $id напрямую вставляется в строку с SQL-запросом и может содержать инъекцию (искусственное завершение текста одного запроса символом комментария и начало следующего запроса злоумышленников)

**Задание 3**

Исправленный код в файле Task_2_patch.php. Статический анализатор SonarCloud не находит уязвимость, если изменить инициализацию переменной $id, добавив функцию real_escape_string(), которая экранирует специальные символы в строке для использования в SQL-выражении, используя текущий набор символов соединения:
*$id = real_escape_string($_GET[ 'id' ])*
![image](https://github.com/larichevams/RBPO_Sem7_Practice4/assets/71451332/136ae444-0402-42f6-83c0-99834000201f)

**Задание 4**
Утилита sqlmap выявила, что поле 'id' в базе данных является уязвимым к SQL-инъекциям:
![image](https://github.com/larichevams/RBPO_Sem7_Practice4/assets/71451332/f2367da0-a8d0-4c98-8d02-850b976d9d30)

