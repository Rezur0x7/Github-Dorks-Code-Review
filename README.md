# Github Dorks - CodeReview
Github regex searches meant to facilitate code review directly in github repos. Some regexes are formatted according to the input expected in 'grep.app'.

- PHP Command Execution: `(exec|passthru|system|exec|popen|proc_open|preg_replace)\(`
- PHP Code Execution: `(eval|assert|include_once|include|require_once|require)\(`
- PHP XSS: `/\becho\b.*\$_GET\b/` or `/echo\s+\$_REQUEST/`
- PHP XSS: `/^.*\becho\s+\$_GET\b.*$/`
- PHP XSS (most FP-prone): `/^.*\becho\s+\$\b.*$/`
- PHP SQL Injection: `/(SELECT|INSERT|UPDATE|DELETE)\s(.*\$_POST|.*\$_GET|.*\$_REQUEST)/`
- PHP OS Command Injection: `/(exec\(|system\(|shell_exec\(|passthru\()(.*\$_POST|.*\$_GET|.*\$_REQUEST)/`
- Host Header Injection (Node.js & PHP): `req.headers.host path:*pass*` and `/\$_SERVER\['host'\]|gethostname\(\).*(reset|forgot)/`
- .NET Host Header Injection: `/(Request\.Headers\["Host"\]|Request\.Host\.Value|HttpContext\.Current\.Request\.Headers\["Host"\]|HttpContext\.Request\.Host\.Value)/ forgot`
- Host Header Injection generic: `host path:**/*forgot*/**`
- Insecure Deserialization in PHP: `/(unserialize\()(.*\$_POST|.*\$_GET|.*\$_REQUEST)/`
- Insecure Deserialization in Python: `(yaml|pickle)+\.load\s*\(`
