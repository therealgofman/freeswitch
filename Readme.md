## Патчи для FreeSwitch версии 1.6.5
Патчи тестировались на версии 1.6.5, под текущий релиз возможно нужно адаптировать, а возможно данный функционал уже завезли (но это не точно :-D).

Патч **add_support_regex_for_variables_sent_to_radius.diff** добавляет возможность изменять переменные, отправляемые на сервер radius, с помощью регулярного выражения (как в диалплане).
Пример использования в mod_xml_radius.conf:

    <param name="Calling-Station-Id" variable="username" format="%s"/>
    <Calling-Station-Id>
    <rule name="first rule for correct">
    <condition variable="username" result="343$1" regex="^(\d{7})$"/>
    </rule>
    </Calling-Station-Id>

Патч **add_support_context_for_unauth_call_and_timeout_request_to_radius.diff**
добавляет поддержу контекста для неавторизованного вызова и таймаута запроса.
Пример использования в mod_xml_radius.conf:

    <global>
    <param name="unauth_context" value="unauth"/>
    <param name="timeout_context" value="timeout"/>
    </global>

