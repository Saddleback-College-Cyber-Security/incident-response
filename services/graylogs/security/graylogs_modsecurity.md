# ModSecurity

source: https://docs.graylog.org/en/3.2/pages/secure/sec_mod_security.html

ModSecurity is an open source web application firewall that can be used in with the Apache and Nginx web servers.

If Graylog is configured behind a web server that uses ModSecurity, some configuration have to be made.

Some distributions (for example RHEL 7.x) ship with older rule sets that do not allow the MIME type **application/json** to be used in requests. This can be fixed by modifying the variable tx.allowed\_request\_content\_type:


    # Allow application/json
    SecRule REQUEST_URI "@beginsWith /" \
      "id:'000001', \
      phase:1, \
      t:none, \
    setvar:'tx.allowed_request_content_type=application/x-www-form-urlencoded|multipart/form-data|text/xml|application/xml|application/x-amf|application/json|application/octet-stream', \
      nolog, \
      pass"

Load balancers accessing **/system/lbstatus** rarely provide the ordinary HTTP headers **Host**, **Accept**, or **User-Agent**. The default rules disallow requests that are missing the mentioned headers. They should be explicitly allowed:

    # Host header
    SecRule REQUEST_URI "@beginsWith /system/lbstatus" \
      "id:'000002', \
      phase:2, \
      t:none, \
      ctl:ruleRemoveById=960008, \
      nolog, \
      pass"
    # Accept header
    SecRule REQUEST_URI "@beginsWith /system/lbstatus" \
      "id:'000003', \
      phase:2, \
      t:none, \
      ctl:ruleRemoveById=960015, \
      nolog, \
      pass"
    # User agent header
    SecRule REQUEST_URI "@beginsWith /system/lbstatus" \
      "id:'000004', \
      phase:2, \
      t:none, \
      ctl:ruleRemoveById=960009, \
      nolog, \
      Pass"

The HTTP verb DELETE is usually forbidden by default. It should be explicitly allowed for requests to **/api/**:

    # Enable DELETE for /api/
    SecRule REQUEST_URI "@beginsWith /api/" \
      "id:'000005', \
      phase:1, \
      t:none, \
      setvar:'tx.allowed_methods=GET HEAD POST OPTIONS DELETE', \
      nolog, \
      pass"

ModSecurity ships by default with strict rules against SQL injection. The query strings used in Graylog searches trigger those rules, breaking all search functionality.


    # Disable SQL injection rules
    SecRuleRemoveById 981173
    SecRuleRemoveById 960024
    SecRuleRemoveById 981318
    SecRuleRemoveById 981257

