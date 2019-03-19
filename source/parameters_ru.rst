Список параметров
~~~~~~~~~~~~~~~~~

0    uint32_t startTime //from 2000 datetime
1    uint32_t endTime;  ///in seconds
2    uint8_t                mode;///avtoMode=0, manualMode=1
3    uint8_t                controlType;//floorControl=0, airControl=1, advancedControl=2
4    int8_t                manualAirTemperature;     ///in   C ()
5    int8_t                manualFloorTemperature; ///in   C
6    int8_t                awayAirTemperature;     ///in   C
7    int8_t                awayFloorTemperature;     ///in   C
8    uint8_t                comfortAirTemperature;        ///in  C
9    uint8_t                economAirTemperature;        ///in  C
10     uint8_t                nightAirTemperature;        ///in  C
11    uint8_t                comfortFloorTemperature;    ///in  C
12    uint8_t                economFloorTemperature;        ///in  C
13     uint8_t                nightFloorTemperature;        ///in  C

14    uint8_t                minTempAdvancedMode;       ///floor limit for temperature in advanced mode C
15    uint8_t                maxTempAdvancedMode;    ///floor limit for temperature in advanced mode C

16    uint8_t             numberOfWeekends;    ///no comment (0, 1, 2)
17    uint8_t                power; /// от 0 до 1,50 кВт шаг 10 Вт, выше 20 Вт
17    uint16_t                power; /// от 0 до 1,50 кВт шаг 10 Вт, выше 20 Вт
18    uint8_t                sensorType; //th4k7Type, th6p8kType, th10kType, th12kType, th15kType, th33kType, th47kType,
19    uint8_t                histeresis; //in 1/10 C (0...25,5)
20    int8_t                airCorrection; /// 1/10 C 1-10
21    int8_t                floorCorrection; /// 1/10 C 1-10
22    uint8_t                 language;    ///no comment english, russian, german
23    uint8_t                brightness; ///in percent/10
24    uint8_t                contrast; ///in percent/5
25    uint8_t                propKoef;/// в минутах 30 минутного цикла работы в пропорциональном режиме когда нет возможности измерять температуру
26    int8_t                upperLimit;//in C for all controlTypes
27    int8_t                lowerLimit;//in C for all controlTypes
28   uint8_t                            number of schedule period // number
29    uint8_t                tempTemperature;     ///in
30   uint8_t                              xtest result; //bit array

33   int8_t                            upperAirLimit;//in C
34   int8_t                            lowerAirLimit;//in C

35    Uint16                upperU;///верхний порог срабатывания по напряжению, in V
36     Uint8                lowerU;///нижний порог срабатывания по напряжению, in V
37    Uint8                upperP;///порог срабатывания по мощности, in 100W
38    Uint16                upperI;///верхний порог срабатывания по току, in 1/10 A
39    Uint16                middleI;///средний порог срабатывания по току, in 1/10 A
40    Uint16                lowerI;///нижний порог срабатывания по току, in 1/10 A
41     Uint16                tOnDelay;///задержка на включение реле в секундах
42     Uint8                tOffDelay;///задержка на выключение реле при превышении верхнего предела по току или мощности, in seconds
43     Uint8                middleITime;///задержка на выключение реле при превышении среднего предела тока, in 0.1 seconds
44     Uint8                lowerITime;///задержка на выключение реле при токе ниже нижнего предела, in 0.1 seconds
45    Uint16                lowVoltageTime;///длительность провала напряжения in 0.1 seconds

46     Int8                correctionsU;///поправка вольтметра, in Volts
47     Int8                correctionsI;///поправка амперметра, in %

48     Uint8                repTimes;///кол-во отлючений реле по току или напряжению до блокировки устройства, in times
49     Uint8                powerType;///тип контролируемой мощности//0 - активная(Вт), 1 - реактивная(ВАр), 2 - полная(ВА)
50     Uint8                showType;///тип отображаемого параметра//0 - ток, 1 - акт. мощн, 2 - реакт. мощн, 3 - полная мощн, 4 - косинус фи
51     Uint8                sensorСontrolNumber;/// номер удалённого датчика для контроля температуры

112     bool                proMode    ///профессиональная модель задержки на выключение по напряжению
113     boo                voltageStableDelay///задержка на включение реле считает с момента нормализации напряжения
114     bool                            androidBlock /// блокировка любых изменений настроек через offlineApi
115     bool                            cloudBlock /// блокировка любых изменений настроек и перепрошивки через облако

116     bool                useContactorControl /// нагрузка через контактор, только учёт электроэнергии
117     bool                NCContactControl    /// инвертированное реле

118     bool                coolingControlWay /// режим нагрев/охлаждения
119     bool                useExtendedPeriod /// использование расширенного расписания
120     bool                useNightTemp      /// использование ночной температуры
121     bool                preControl;       /// предварительный контроль
122     bool                windowOpenControl;/// режим открытого окна
123     bool                rtcStop;          ///остановка/запуск часов в конце/начале сезона
124     bool                childrenLock;     /// защита от детей
125     bool                powerOff;         ///выключение
126    uint8_t                         rfAddress;        /// адрес рф                 (не актуально)
127    int8_t                          rfCorrection;     //change offset cc1101 reg C (не актуально)

Редактировать эту секцию
Список типов параметров
0 CStringType
1 Int8
2 Uint8
3 Int16
4 Uint16
5 Int32
6 Uint32
7 Bool,
8 Timetable