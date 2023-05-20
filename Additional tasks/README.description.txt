Задания:
1. Написать консольное приложение на любом удобном для Вас языке программирования, которое парсит структуру любого языка программирования, либо SQL (PL/SQL, T/SQL).
   Можно воспользоваться готовыми грамматиками из проекта ANTLR4: https://github.com/antlr/grammars-v4
   Результатом парсинга должен быть xml, либо json-файл.

   Пример:
   На входе будет отрывок кода из документации Oracle (файл с примерами: oracle.example.code.sql):
   CREATE TABLE log (
      log_id   NUMBER(6),
      up_date  DATE,
      new_sal  NUMBER(8,2),
      old_sal  NUMBER(8,2)
   );

   Результат (в данном случае) будет в виде xml-файла:
    <?xml version="1.0"?>
    <sql_script>
        <unit_statement>
            <create_table>
                <T__CREATE line="1" pos="0">CREATE</T__CREATE>
                <T__TABLE line="1" pos="7">TABLE</T__TABLE>
                <tableview_name>
                    <identifier>
                        <id_expression>
                            <regular_id>
                                <non_reserved_keywords_pre12c>
                                    <T__LOG line="1" pos="13">log</T__LOG>
                                </non_reserved_keywords_pre12c>
                            </regular_id>
                        </id_expression>
                    </identifier>
                </tableview_name>
                <relational_table>
                    <T__LEFT_PAREN line="1" pos="17">(</T__LEFT_PAREN>
                    <relational_property>
                        <column_definition>
                            <column_name>
                                <identifier>
                                    <id_expression>
                                        <regular_id>
                                            <T__REGULAR_ID line="2" pos="2">log_id</T__REGULAR_ID>
                                        </regular_id>
                                    </id_expression>
                                </identifier>
                            </column_name>
                            <datatype>
                                <native_datatype_element>
                                    <T__NUMBER line="2" pos="11">NUMBER</T__NUMBER>
                                </native_datatype_element>
                                <precision_part>
                                    <T__LEFT_PAREN line="2" pos="17">(</T__LEFT_PAREN>
                                    <numeric>
                                        <T__UNSIGNED_INTEGER line="2" pos="18">6</T__UNSIGNED_INTEGER>
                                    </numeric>
                                    <T__RIGHT_PAREN line="2" pos="19">)</T__RIGHT_PAREN>
                                </precision_part>
                            </datatype>
                        </column_definition>
                    </relational_property>
                    <T__COMMA line="2" pos="20">,</T__COMMA>
                    <relational_property>
                        <column_definition>
                            <column_name>
                                <identifier>
                                    <id_expression>
                                        <regular_id>
                                            <T__REGULAR_ID line="3" pos="2">up_date</T__REGULAR_ID>
                                        </regular_id>
                                    </id_expression>
                                </identifier>
                            </column_name>
                            <datatype>
                                <native_datatype_element>
                                    <T__DATE line="3" pos="11">DATE</T__DATE>
                                </native_datatype_element>
                            </datatype>
                        </column_definition>
                    </relational_property>
                    <T__COMMA line="3" pos="15">,</T__COMMA>
                    <relational_property>
                        <column_definition>
                            <column_name>
                                <identifier>
                                    <id_expression>
                                        <regular_id>
                                            <T__REGULAR_ID line="4" pos="2">new_sal</T__REGULAR_ID>
                                        </regular_id>
                                    </id_expression>
                                </identifier>
                            </column_name>
                            <datatype>
                                <native_datatype_element>
                                    <T__NUMBER line="4" pos="11">NUMBER</T__NUMBER>
                                </native_datatype_element>
                                <precision_part>
                                    <T__LEFT_PAREN line="4" pos="17">(</T__LEFT_PAREN>
                                    <numeric>
                                        <T__UNSIGNED_INTEGER line="4" pos="18">8</T__UNSIGNED_INTEGER>
                                    </numeric>
                                    <T__COMMA line="4" pos="19">,</T__COMMA>
                                    <numeric>
                                        <T__UNSIGNED_INTEGER line="4" pos="20">2</T__UNSIGNED_INTEGER>
                                    </numeric>
                                    <T__RIGHT_PAREN line="4" pos="21">)</T__RIGHT_PAREN>
                                </precision_part>
                            </datatype>
                        </column_definition>
                    </relational_property>
                    <T__COMMA line="4" pos="22">,</T__COMMA>
                    <relational_property>
                        <column_definition>
                            <column_name>
                                <identifier>
                                    <id_expression>
                                        <regular_id>
                                            <T__REGULAR_ID line="5" pos="2">old_sal</T__REGULAR_ID>
                                        </regular_id>
                                    </id_expression>
                                </identifier>
                            </column_name>
                            <datatype>
                                <native_datatype_element>
                                    <T__NUMBER line="5" pos="11">NUMBER</T__NUMBER>
                                </native_datatype_element>
                                <precision_part>
                                    <T__LEFT_PAREN line="5" pos="17">(</T__LEFT_PAREN>
                                    <numeric>
                                        <T__UNSIGNED_INTEGER line="5" pos="18">8</T__UNSIGNED_INTEGER>
                                    </numeric>
                                    <T__COMMA line="5" pos="19">,</T__COMMA>
                                    <numeric>
                                        <T__UNSIGNED_INTEGER line="5" pos="20">2</T__UNSIGNED_INTEGER>
                                    </numeric>
                                    <T__RIGHT_PAREN line="5" pos="21">)</T__RIGHT_PAREN>
                                </precision_part>
                            </datatype>
                        </column_definition>
                    </relational_property>
                    <T__RIGHT_PAREN line="6" pos="0">)</T__RIGHT_PAREN>
                </relational_table>
                <T__SEMICOLON line="6" pos="1">;</T__SEMICOLON>
            </create_table>
        </unit_statement>
    </sql_script>
2. Для примера кода из предыдущего задания (таблица log) необходимо преобразовать в класс (Java, C#) любым удобным для Вас способом.
   2.1 Имя таблицы переходит в имя класса.
   2.2 Колонки таблицы переходят в поля класса.
   
   Пример:
   CREATE TABLE log (
     log_id   NUMBER(6),
     up_date  DATE,
     new_sal  NUMBER(8,2),
     old_sal  NUMBER(8,2)
   );

   Результат:
   Java-класс (в данном случае): Log.java
   public class Log {
      Integer log_id;
      Timestamp up_date;
      Integer new_sal;
      Integer old_sal;
   }
