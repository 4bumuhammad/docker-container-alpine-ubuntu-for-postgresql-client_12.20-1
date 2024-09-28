## 🪭 Container Environment Linux for postgresql-client

&nbsp;

**2024,September 27: Check postgresql version** <br />
⌘ [onpremise sit/uat] <b>Powerbiz</b>
<pre>
SELECT version()
output: PostgreSQL 12.8 on x86_64-pc-linux-gnu, 
        compiled by gcc (Debian 8.3.0-6) 8.3.0, 64-bit
</pre>

<br />

⌘ [production] <b>Powerbiz</b>
<pre>
SELECT version()
output: PostgreSQL 12.16 on aarch64-unknown-linux-gnu, 
        compiled by aarch64-unknown-linux-gnu-gcc (GCC) 9.5.0, 64-bit
</pre>

&nbsp;

🟡 **[ Alpine ]** <br />
Standardized containers for postgresql-client [ <a href="./pg-client-alpine/README.md" title="Docker Container pg-client-alpine" >Open</a> ].

&nbsp;

🟡 **[ Ubuntu ]**  <br />
Standardized containers for postgresql-client=12.20-1.pgdg22.04+1 [ <a href="./pg-client-ubuntu/README.md" title="Docker Container pg-client-ubuntu" >Open</a> ].
