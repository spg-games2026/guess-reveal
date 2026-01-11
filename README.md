# Guess-Reveal

Small memory match game built with plain HTML/CSS/JS.

Run locally:

- Use a static server (recommended):

  - PowerShell fallback (no install):
    ```powershell
    $root='C:\Users\Anu\Desktop\guess-reveal'; $listener=[System.Net.HttpListener]::new(); $listener.Prefixes.Add('http://localhost:8000/'); $listener.Start(); while($listener.IsListening){ $ctx=$listener.GetContext(); $req=$ctx.Request; $path=$req.Url.LocalPath.TrimStart('/'); if([string]::IsNullOrEmpty($path)){ $file=Join-Path $root 'index.html' } else { $file=Join-Path $root $path } if(Test-Path $file){ $bytes=[System.IO.File]::ReadAllBytes($file); $ctx.Response.ContentLength64=$bytes.Length; $ctx.Response.OutputStream.Write($bytes,0,$bytes.Length) } else { $ctx.Response.StatusCode=404 } $ctx.Response.Close() }
    ```

- Or install Python/Node and run one of the single-line servers:

  ```powershell
  python -m http.server 8000
  # or
  npx http-server -p 8000
  ```

License: MIT (or change as needed)
