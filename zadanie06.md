PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose exec backend pytest -v
================================= test session starts ==================================
platform linux -- Python 3.12.16, pytest-8.4.2, pluggy-1.7.0 -- /usr/local/bin/python3.12
cachedir: .pytest_cache
rootdir: /app
collected 8 items                                                                      

tests/test_check.py::test_leaked_hash_is_found PASSED                            [ 12%]
tests/test_check.py::test_unknown_hash_is_not_found PASSED                       [ 25%]
tests/test_check.py::test_missing_hash_field PASSED                              [ 37%]
tests/test_check.py::test_plaintext_password_is_rejected PASSED                  [ 50%]
tests/test_check.py::test_uppercase_hash_is_found PASSED                         [ 62%]
tests/test_check.py::test_short_hash_is_rejected PASSED                          [ 75%]
tests/test_check.py::test_non_hex_40_char_hash_is_rejected PASSED                [ 87%]
tests/test_check.py::test_non_json_body_is_rejected PASSED                       [100%]

================================== 8 passed in 0.11s ===================================
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 



================================= test session starts ==================================
platform linux -- Python 3.12.16, pytest-8.4.2, pluggy-1.7.0 -- /usr/local/bin/python3.12
cachedir: .pytest_cache
rootdir: /app
collected 8 items                                                                      

tests/test_check.py::test_leaked_hash_is_found PASSED                            [ 12%]
tests/test_check.py::test_unknown_hash_is_not_found PASSED                       [ 25%]
tests/test_check.py::test_missing_hash_field PASSED                              [ 37%]
tests/test_check.py::test_plaintext_password_is_rejected PASSED                  [ 50%]
tests/test_check.py::test_uppercase_hash_is_found FAILED                         [ 62%]
tests/test_check.py::test_short_hash_is_rejected PASSED                          [ 75%]
tests/test_check.py::test_non_hex_40_char_hash_is_rejected PASSED                [ 87%]
tests/test_check.py::test_non_json_body_is_rejected PASSED                       [100%]

======================================= FAILURES =======================================
_____________________________ test_uppercase_hash_is_found _____________________________

client = <FlaskClient <Flask 'app'>>

    def test_uppercase_hash_is_found(client):
        response = client.post("/check", json={"hash": LEAKED.upper()})
>       assert response.status_code == 200
E       assert 400 == 200
E        +  where 400 = <WrapperTestResponse streamed [400 BAD REQUEST]>.status_code

tests/test_check.py:28: AssertionError
=============================== short test summary info ================================
FAILED tests/test_check.py::test_uppercase_hash_is_found - assert 400 == 200
============================= 1 failed, 7 passed in 0.16s ==============================

What's next:
    Debug this Compose error with Gordon → docker ai "help me fix this compose error"
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 










PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> # Windows PowerShell
>> '{"hash":"7c4a8d09ca3762af61e59520943dc26494f8941b"}' | curl.exe -s -o blad.html -w "HTTP %{http_code}\n" -X POST http://localhost:8080/api/check -H "Content-Type: application/json" -d '@-'
>> 
HTTP 500


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose logs --tail 20 backend
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:02] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:08] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:13] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:18] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:23] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:28] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:33] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:38] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:43] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:48] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:53] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:44:59] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:04] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:09] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:14] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:19] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:24] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:29] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:34] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [25/Nov/2026 19:45:39] "GET /health HTTP/1.1" 200 -
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 




PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker inspect --format '{{.State.Status}} {{.State.ExitCode}}' metody_wirt_lab-backend-1
exited 1
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 



PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose ps -a    
NAME                         IMAGE                      COMMAND                  SERVICE    CREATED          STATUS                          PORTS
metody_wirt_lab-backend-1    metody_wirt_lab-backend    "flask --app app run…"   backend    50 minutes ago   Exited (1) About a minute ago   
metody_wirt_lab-db-1         postgres:16-alpine         "docker-entrypoint.s…"   db         50 minutes ago   Exited (0) 5 minutes ago        
metody_wirt_lab-frontend-1   metody_wirt_lab-frontend   "/docker-entrypoint.…"   frontend   50 minutes ago   Up 50 minutes                   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 



PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> Get-Content .\blad.html -Head 25
<!doctype html>
<html lang=en>
  <head>
    <title>psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

 // Werkzeug Debugger</title>
    <link rel="stylesheet" href="?__debugger__=yes&amp;cmd=resource&amp;f=style.css">
    <link rel="shortcut icon"
        href="?__debugger__=yes&amp;cmd=resource&amp;f=console.png">
    <script src="?__debugger__=yes&amp;cmd=resource&amp;f=debugger.js"></script>
    <script>
      var CONSOLE_MODE = false,
          EVALEX = false,
          EVALEX_TRUSTED = false,
          SECRET = "Xhviw3BLoNb7aHbXZlhy";
    </script>
  </head>
  <body style="background-color: #fff">
    <div class="debugger">
<h1>OperationalError</h1>
<div class="detail">
  <p class="errormsg">psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

</p>
</div>
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 
















<!doctype html>
<html lang=en>
  <head>
    <title>psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

 // Werkzeug Debugger</title>
    <link rel="stylesheet" href="?__debugger__=yes&amp;cmd=resource&amp;f=style.css">
    <link rel="shortcut icon"
        href="?__debugger__=yes&amp;cmd=resource&amp;f=console.png">
    <script src="?__debugger__=yes&amp;cmd=resource&amp;f=debugger.js"></script>
    <script>
      var CONSOLE_MODE = false,
          EVALEX = false,
          EVALEX_TRUSTED = false,
          SECRET = "Xhviw3BLoNb7aHbXZlhy";
    </script>
  </head>
  <body style="background-color: #fff">
    <div class="debugger">
<h1>OperationalError</h1>
<div class="detail">
  <p class="errormsg">psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

</p>
</div>
<h2 class="traceback">Traceback <em>(most recent call last)</em></h2>
<div class="traceback">
  <h3></h3>
  <ul><li><div class="frame" id="frame-128562872439216">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/flask/app.py"</cite>,
      line <em class="line">1536</em>,
      in <code class="function">__call__</code></h4>
  <div class="source library"><pre class="line before"><span class="ws">    </span>) -&gt; cabc.Iterable[bytes]:</pre>
<pre class="line before"><span class="ws">        </span>&#34;&#34;&#34;The WSGI server calls the Flask application object as the</pre>
<pre class="line before"><span class="ws">        </span>WSGI application. This calls :meth:`wsgi_app`, which can be</pre>
<pre class="line before"><span class="ws">        </span>wrapped to apply middleware.</pre>
<pre class="line before"><span class="ws">        </span>&#34;&#34;&#34;</pre>
<pre class="line current"><span class="ws">        </span>return self.wsgi_app(environ, start_response)
<span class="ws">        </span>       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^</pre></div>
</div>

<li><div class="frame" id="frame-128562872439072">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/flask/app.py"</cite>,
      line <em class="line">1514</em>,
      in <code class="function">wsgi_app</code></h4>
  <div class="source library"><pre class="line before"><span class="ws">            </span>try:</pre>
<pre class="line before"><span class="ws">                </span>ctx.push()</pre>
<pre class="line before"><span class="ws">                </span>response = self.full_dispatch_request()</pre>
<pre class="line before"><span class="ws">            </span>except Exception as e:</pre>
<pre class="line before"><span class="ws">                </span>error = e</pre>
<pre class="line current"><span class="ws">                </span>response = self.handle_exception(e)
<span class="ws">                </span>           ^^^^^^^^^^^^^^^^^^^^^^^^</pre>
<pre class="line after"><span class="ws">            </span>except:  # noqa: B001</pre>
<pre class="line after"><span class="ws">                </span>error = sys.exc_info()[1]</pre>
<pre class="line after"><span class="ws">                </span>raise</pre>
<pre class="line after"><span class="ws">            </span>return response(environ, start_response)</pre>
<pre class="line after"><span class="ws">        </span>finally:</pre></div>
</div>

<li><div class="frame" id="frame-128562872440944">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/flask/app.py"</cite>,
      line <em class="line">1511</em>,
      in <code class="function">wsgi_app</code></h4>
  <div class="source library"><pre class="line before"><span class="ws">        </span>ctx = self.request_context(environ)</pre>
<pre class="line before"><span class="ws">        </span>error: BaseException | None = None</pre>
<pre class="line before"><span class="ws">        </span>try:</pre>
<pre class="line before"><span class="ws">            </span>try:</pre>
<pre class="line before"><span class="ws">                </span>ctx.push()</pre>
<pre class="line current"><span class="ws">                </span>response = self.full_dispatch_request()
<span class="ws">                </span>           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^</pre>
<pre class="line after"><span class="ws">            </span>except Exception as e:</pre>
<pre class="line after"><span class="ws">                </span>error = e</pre>
<pre class="line after"><span class="ws">                </span>response = self.handle_exception(e)</pre>
<pre class="line after"><span class="ws">            </span>except:  # noqa: B001</pre>
<pre class="line after"><span class="ws">                </span>error = sys.exc_info()[1]</pre></div>
</div>

<li><div class="frame" id="frame-128562872441088">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/flask/app.py"</cite>,
      line <em class="line">919</em>,
      in <code class="function">full_dispatch_request</code></h4>
  <div class="source library"><pre class="line before"><span class="ws">            </span>request_started.send(self, _async_wrapper=self.ensure_sync)</pre>
<pre class="line before"><span class="ws">            </span>rv = self.preprocess_request()</pre>
<pre class="line before"><span class="ws">            </span>if rv is None:</pre>
<pre class="line before"><span class="ws">                </span>rv = self.dispatch_request()</pre>
<pre class="line before"><span class="ws">        </span>except Exception as e:</pre>
<pre class="line current"><span class="ws">            </span>rv = self.handle_user_exception(e)
<span class="ws">            </span>     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^</pre>
<pre class="line after"><span class="ws">        </span>return self.finalize_request(rv)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def finalize_request(</pre>
<pre class="line after"><span class="ws">        </span>self,</pre>
<pre class="line after"><span class="ws">        </span>rv: ft.ResponseReturnValue | HTTPException,</pre></div>
</div>

<li><div class="frame" id="frame-128562872441232">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/flask/app.py"</cite>,
      line <em class="line">917</em>,
      in <code class="function">full_dispatch_request</code></h4>
  <div class="source library"><pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">        </span>try:</pre>
<pre class="line before"><span class="ws">            </span>request_started.send(self, _async_wrapper=self.ensure_sync)</pre>
<pre class="line before"><span class="ws">            </span>rv = self.preprocess_request()</pre>
<pre class="line before"><span class="ws">            </span>if rv is None:</pre>
<pre class="line current"><span class="ws">                </span>rv = self.dispatch_request()
<span class="ws">                </span>     ^^^^^^^^^^^^^^^^^^^^^^^</pre>
<pre class="line after"><span class="ws">        </span>except Exception as e:</pre>
<pre class="line after"><span class="ws">            </span>rv = self.handle_user_exception(e)</pre>
<pre class="line after"><span class="ws">        </span>return self.finalize_request(rv)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def finalize_request(</pre></div>
</div>

<li><div class="frame" id="frame-128562872441376">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/flask/app.py"</cite>,
      line <em class="line">902</em>,
      in <code class="function">dispatch_request</code></h4>
  <div class="source library"><pre class="line before"><span class="ws">            </span>and req.method == &#34;OPTIONS&#34;</pre>
<pre class="line before"><span class="ws">        </span>):</pre>
<pre class="line before"><span class="ws">            </span>return self.make_default_options_response()</pre>
<pre class="line before"><span class="ws">        </span># otherwise dispatch to the handler for that endpoint</pre>
<pre class="line before"><span class="ws">        </span>view_args: dict[str, t.Any] = req.view_args  # type: ignore[assignment]</pre>
<pre class="line current"><span class="ws">        </span>return self.ensure_sync(self.view_functions[rule.endpoint])(**view_args)  # type: ignore[no-any-return]
<span class="ws">        </span>       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def full_dispatch_request(self) -&gt; Response:</pre>
<pre class="line after"><span class="ws">        </span>&#34;&#34;&#34;Dispatches the request and on top of that performs request</pre>
<pre class="line after"><span class="ws">        </span>pre and postprocessing as well as HTTP exception catching and</pre>
<pre class="line after"><span class="ws">        </span>error handling.</pre></div>
</div>

<li><div class="frame" id="frame-128562872441520">
  <h4>File <cite class="filename">"/app/app.py"</cite>,
      line <em class="line">38</em>,
      in <code class="function">check</code></h4>
  <div class="source "><pre class="line before"><span class="ws">        </span>return jsonify({&#34;error&#34;: &#34;pole &#39;hash&#39; musi być skrótem SHA-1 (40 znaków hex)&#34;}), 400</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">    </span># Pełny SHA-1 popularnego hasła łatwo odwrócić - w logu tylko początek</pre>
<pre class="line before"><span class="ws">    </span>print(f&#34;check: hash={h[:5]}...&#34;, flush=True)</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line current"><span class="ws">    </span>conn = connect()
<span class="ws">    </span>       ^^^^^^^^^</pre>
<pre class="line after"><span class="ws">    </span>try:</pre>
<pre class="line after"><span class="ws">        </span>with conn.cursor() as cur:</pre>
<pre class="line after"><span class="ws">            </span># %s = parametr zapytania: wartość h nigdy nie staje się częścią kodu SQL</pre>
<pre class="line after"><span class="ws">            </span>cur.execute(&#34;SELECT EXISTS (SELECT 1 FROM leaked_hashes WHERE hash = %s)&#34;, (h,))</pre>
<pre class="line after"><span class="ws">            </span>found = cur.fetchone()[0]</pre></div>
</div>

<li><div class="frame" id="frame-128562872441808">
  <h4>File <cite class="filename">"/app/app.py"</cite>,
      line <em class="line">11</em>,
      in <code class="function">connect</code></h4>
  <div class="source "><pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws"></span>app = Flask(__name__)</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws"></span>def connect():</pre>
<pre class="line before"><span class="ws">    </span># Dane połączenia przychodzą ze zmiennych środowiskowych ustawionych w docker-compose.yml</pre>
<pre class="line current"><span class="ws">    </span>return psycopg2.connect(
<span class="ws">    </span>       </pre>
<pre class="line after"><span class="ws">        </span>host=os.environ[&#34;DB_HOST&#34;],</pre>
<pre class="line after"><span class="ws">        </span>dbname=os.environ[&#34;DB_NAME&#34;],</pre>
<pre class="line after"><span class="ws">        </span>user=os.environ[&#34;DB_USER&#34;],</pre>
<pre class="line after"><span class="ws">        </span>password=os.environ[&#34;DB_PASSWORD&#34;],</pre>
<pre class="line after"><span class="ws">    </span>)</pre></div>
</div>

<li><div class="frame" id="frame-128562872441952">
  <h4>File <cite class="filename">"/usr/local/lib/python3.12/site-packages/psycopg2/__init__.py"</cite>,
      line <em class="line">122</em>,
      in <code class="function">connect</code></h4>
  <div class="source library"><pre class="line before"><span class="ws">        </span>kwasync[&#39;async&#39;] = kwargs.pop(&#39;async&#39;)</pre>
<pre class="line before"><span class="ws">    </span>if &#39;async_&#39; in kwargs:</pre>
<pre class="line before"><span class="ws">        </span>kwasync[&#39;async_&#39;] = kwargs.pop(&#39;async_&#39;)</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">    </span>dsn = _ext.make_dsn(dsn, **kwargs)</pre>
<pre class="line current"><span class="ws">    </span>conn = _connect(dsn, connection_factory=connection_factory, **kwasync)
<span class="ws">    </span>       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^</pre>
<pre class="line after"><span class="ws">    </span>if cursor_factory is not None:</pre>
<pre class="line after"><span class="ws">        </span>conn.cursor_factory = cursor_factory</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>return conn</pre></div>
</div>
</ul>
  <blockquote>psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

</blockquote>
</div>

<div class="plain">
    <p>
      This is the Copy/Paste friendly version of the traceback.
    </p>
    <textarea cols="50" rows="10" name="code" readonly>Traceback (most recent call last):
  File &#34;/usr/local/lib/python3.12/site-packages/flask/app.py&#34;, line 1536, in __call__
    return self.wsgi_app(environ, start_response)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File &#34;/usr/local/lib/python3.12/site-packages/flask/app.py&#34;, line 1514, in wsgi_app
    response = self.handle_exception(e)
               ^^^^^^^^^^^^^^^^^^^^^^^^
  File &#34;/usr/local/lib/python3.12/site-packages/flask/app.py&#34;, line 1511, in wsgi_app
    response = self.full_dispatch_request()
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File &#34;/usr/local/lib/python3.12/site-packages/flask/app.py&#34;, line 919, in full_dispatch_request
    rv = self.handle_user_exception(e)
         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File &#34;/usr/local/lib/python3.12/site-packages/flask/app.py&#34;, line 917, in full_dispatch_request
    rv = self.dispatch_request()
         ^^^^^^^^^^^^^^^^^^^^^^^
  File &#34;/usr/local/lib/python3.12/site-packages/flask/app.py&#34;, line 902, in dispatch_request
    return self.ensure_sync(self.view_functions[rule.endpoint])(**view_args)  # type: ignore[no-any-return]
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File &#34;/app/app.py&#34;, line 38, in check
    conn = connect()
           ^^^^^^^^^
  File &#34;/app/app.py&#34;, line 11, in connect
    return psycopg2.connect(
           ^^^^^^^^^^^^^^^^^
  File &#34;/usr/local/lib/python3.12/site-packages/psycopg2/__init__.py&#34;, line 122, in connect
    conn = _connect(dsn, connection_factory=connection_factory, **kwasync)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

</textarea>
</div>
<div class="explanation">
  The debugger caught an exception in your WSGI application.  You can now
  look at the traceback which led to the error.  <span class="nojavascript">
  If you enable JavaScript you can also use additional features such as code
  execution (if the evalex feature is enabled), automatic pasting of the
  exceptions and much more.</span>
</div>
      <div class="footer">
        Brought to you by <strong class="arthur">DON'T PANIC</strong>, your
        friendly Werkzeug powered traceback interpreter.
      </div>
    </div>

    <div class="pin-prompt">
      <div class="inner">
        <h3>Console Locked</h3>
        <p>
          The console is locked and needs to be unlocked by entering the PIN.
          You can find the PIN printed out on the standard output of your
          shell that runs the server.
        <form>
          <p>PIN:
            <input type=text name=pin size=14>
            <input type=submit name=btn value="Confirm Pin">
        </form>
      </div>
    </div>
  </body>
</html>

<!--

Traceback (most recent call last):
  File "/usr/local/lib/python3.12/site-packages/flask/app.py", line 1536, in __call__
    return self.wsgi_app(environ, start_response)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/flask/app.py", line 1514, in wsgi_app
    response = self.handle_exception(e)
               ^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/flask/app.py", line 1511, in wsgi_app
    response = self.full_dispatch_request()
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/flask/app.py", line 919, in full_dispatch_request
    rv = self.handle_user_exception(e)
         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/flask/app.py", line 917, in full_dispatch_request
    rv = self.dispatch_request()
         ^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/flask/app.py", line 902, in dispatch_request
    return self.ensure_sync(self.view_functions[rule.endpoint])(**view_args)  # type: ignore[no-any-return]
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/app/app.py", line 38, in check
    conn = connect()
           ^^^^^^^^^
  File "/app/app.py", line 11, in connect
    return psycopg2.connect(
           ^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/psycopg2/__init__.py", line 122, in connect
    conn = _connect(dsn, connection_factory=connection_factory, **kwasync)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
psycopg2.OperationalError: could not translate host name "db" to address: Name or service not known



-->












</div>
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose ps
NAME                         IMAGE                      COMMAND                  SERVICE    CREATED          STATUS          PORTS
metody_wirt_lab-frontend-1   metody_wirt_lab-frontend   "/docker-entrypoint.…"   frontend   57 minutes ago   Up 57 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> Get-Content .\blad.html -Head 25
<!doctype html>
<html lang=en>
  <head>
    <title>psycopg2.OperationalError: could not translate host name &#34;db&#34; to address: Name or service not known

 // Werkzeug Debugger</title>
    <link rel="stylesheet" href="?__debugger__=yes&amp;cmd=resource&amp;f=style.css">
    <link rel="shortcut icon"
        href="?__debugger__=yes&amp;cmd=resource&amp;f=console.png">
    <script src="?__debugger__=yes&amp;cmd=resource&amp;f=debugger.js"></script>
    <script>
      var CONSOLE_MODE = false,
CONTAINER ID   NAME                         CPU %     MEM USAGE / LIMIT    MEM %     NET I/O           BLOCK I/O         PIDS
b16b568fc1f7   metody_wirt_lab-frontend-1   0.00%     14.19MiB / 7.61GiB   0.18%     78.8kB / 83.8kB   2.47MB / 8.19kB   17
880ebb85d7d9   kind-control-plane           12.20%    906.8MiB / 7.61GiB   11.64%    8.26kB / 6.38kB   723MB / 200MB     439



PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker stats --no-stream

CONTAINER ID   NAME                         CPU %     MEM USAGE / LIMIT    MEM %     NET I/O           BLOCK I/O         PIDS
b16b568fc1f7   metody_wirt_lab-frontend-1   0.00%     14.19MiB / 7.61GiB   0.18%     78.8kB / 83.8kB   2.47MB / 8.19kB   17
880ebb85d7d9   kind-control-plane           12.35%    897.9MiB / 7.61GiB   11.52%    8.26kB / 6.38kB   723MB / 212MB     439
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 























server {
    listen 80;

    # Pliki strony (index.html, style.css, script.js)
    location / {
        root /usr/share/nginx/html;
        index index.html;
    }

    # Wszystko pod /api/ nginx przekazuje do usługi backend w sieci Compose
    location /api/ {
        proxy_pass http://backend:5000/;
    }
}



FROM nginx:alpine
LABEL autor="Anastasiya Drako" data="2026-11-05"
COPY index.html style.css script.js /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> curl.exe -s http://localhost:8080/nginx.conf
server {
    listen 80;

    # Pliki strony (index.html, style.css, script.js)
    location / {
        root /usr/share/nginx/html;
        index index.html;
    }

    # Wszystko pod /api/ nginx przekazuje do usługi backend w sieci Compose
    location /api/ {
        proxy_pass http://backend:5000/;
    }
}
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 














PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose up -d
[+] up 3/3
 ✔ Container metody_wirt_lab-db-1       Healthy                                     1.1s
 ✔ Container metody_wirt_lab-backend-1  Healthy                                     1.6s
 ✔ Container metody_wirt_lab-frontend-1 Started                                     1.8s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 

server {
    listen 80;

    # Pliki strony (index.html, style.css, script.js)
    location / {
        root /usr/share/nginx/html;
        index index.html;
    }

    # Wszystko pod /api/ nginx przekazuje do usługi backend w sieci Compose
    location /api/ {
        proxy_pass http://backend:5000/;
    }
}



PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose up -d
[+] up 3/3
 ✔ Container metody_wirt_lab-db-1       Healthy                                     1.1s
 ✔ Container metody_wirt_lab-backend-1  Healthy                                     1.6s
 ✔ Container metody_wirt_lab-frontend-1 Started                                     1.8s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose restart frontend
[+] restart 0/1
 - Container metody_wirt_lab-frontend-1 Restarting                                  2.2s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 



server {
    listen 80;

    # Pliki strony (index.html, style.css, script.js)
    location / {
        root /usr/share/nginx/html;
        index index.html;
    }

    # Wszystko pod /api/ nginx przekazuje do usługi backend w sieci Compose
    location /api/ {
        proxy_pass http://backend:5000/;
    }
}



FROM nginx:alpine
LABEL autor="Anastasiya Drako" data="2026-11-05"
COPY index.html style.css script.js /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> curl.exe -I http://localhost:8080/nginx.conf
HTTP/1.1 404 Not Found
Server: nginx/1.31.9
Date: Wed, 25 Nov 2026 20:22:56 GMT
Content-Type: text/html
Content-Length: 153
Connection: keep-alive

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 