Телеметрия
~~~~~~~~~~

Телеметрия служит для получения текущего состояния устройства.
Для получения телеметрии отправьте запрос ``{"cmd":4}``. Например, ответ для терморегулятора AX с версией ПО 2.3 будет вида:

.. code-block:: json 

     {
      "sn":"058016000543464839373520000159",
      "t.0":"450","t.1":"416","t.5":"480",
      "m.0":"0","m.1":"3","m.2":"34","m.3":"2",
      "f.0":"1","f.1":"0","f.2":"0","f.3":"0",
      "f.4":"0","f.7":"0","f.8":"0","f.9":"0",
      "f.13":"0","f.14":"0","f.10":"0","f.11":"1",
      "f.12":"0","o.0":"-83","o.1":"6","f.15":"0",
      "par.26":"45","par.27":"5"
     }

``sn`` - серийный номер устройства

``x.n`` - ключ параметра, где ``x`` - группа параметров, ``n`` - номер в группе

Группы параметров:
	* ``t`` - температура в 1/16 °C
		* ``0`` - внутрений датчик перегрева
		* ``1`` - пола
		* ``2`` - воздуха
		* ``3`` - зарезервировано
		* ``4`` - зарезервировано
		* ``5`` - текущая уставка
		* ``6`` - зарезервировано
		* ``7`` - температура МК
	* ``m`` - режимы
		* ``0`` - тип контроля: пол = 0, воздух = 1, расширенный = 2
		* ``1`` - тип управления: по расписанию = 0, ручной = 3, отъезд = 4, временный = 5           
		* ``2`` - номер текущего периода расписания (первый период понедельника = 0, вторника = maxSchedulePeriod...)
		* ``3`` - тип блокировки: нет блокировок = 0, блокировка изменений из облака = 1, блокировка изменений из локальной сети = 2, обе = 3
		* ``4`` - зарезервировано
		* ``5`` - режим работы нагрева (0 - нагрев, 1 - охлаждение)	
	* ``o`` - прочие параметры
		* ``0`` - уровень сигнала Wi-Fi в dBm (-127..128)
		* ``1`` - причина последней перезагрузки. В зависимости от аппаратной версии платформы может быть два типа значений: первый - маска: выключение = 0x04, программный сброс = 0x08, сторожевой таймер = 0x10, низкое напряжение = 0x40. Второе: 9 - программная перезагрузка из-за низкого напряжения питания МК; 3 – программная перезагрузка; 1 - сброс питания.
	* ``par`` - дублирование некоторых параметров устройства
		* ``n`` - номер параметра	
	* ``te`` - дополнительная температура	
	* ``f`` - битовые параметры
		* ``0`` - состояние нагрузки
		* ``1`` - зарезервировано
		* ``2`` - действие ограничения по полу
		* ``3`` - обрыв датчика пола
		* ``4`` - короткое замыкания датчика пола
		* ``5`` - обрыв датчика воздуха
		* ``6`` - короткое замыкания датчика воздуха
		* ``7`` - действие предварительного прогрева
		* ``8`` - действие ф-ции открытого окна
		* ``9`` - внутренний перегрев
		* ``10`` - зарезервировано
		* ``11`` - проблемы с часами
		* ``12`` - нет контроля перегрева
		* ``13`` - пропорциональный режим работы нагрузки
		* ``14`` - используется цифровой датчик пола
		* ``15`` - зарезервировано
		* ``16`` - устройство выключено
		* ``17`` - зарезервировано
		* ``18`` - зарезервировано
		* ``19`` - зарезервировано
		* ``20`` - зарезервировано
		* ``21`` - ошибка датчика zero crossing