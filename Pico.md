#### 1. GET aHEAD
--> Challenge gives a hint about HEAD method. Tried requesting website with HEAD method
```bash
picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}
``` 

#### 2. Cookies
--> Each cookie value gave a different cookies. Changed the value from 0 to 18. At cookie value 18 found flag
==> picoCTF{3v3ry1_l0v3s_c00k135_88acab36}

#### 3. Insp3ct0r
--> Found first part of flag in view source. found 2nd part of flag in .css file. found 3rd part of flag in .js file
==> picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?f10be399}

#### 4. Scavenger Hunt
--> Found first part of flag in view source. found 2nd part of flag in .css file. found 3rd part of flag in robots.txt. found 4th part of flag in .htaccess path. found 5th part of flag in .DS_Store path.
==> picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_a69684fd}

#### 5. Assembly Required 

#### 6. More Cookies

#### 7. where are the robots
--> Visited the robots.txt , which had path for disallow. found the flag in that path.
==> picoCTF{ca1cu1at1ng_Mach1n3s_8028f}

#### 8. logon
--> logged in with default credentials admin:admin . Found a cookie with admin value "False". Changed it to "True" found the flag.
==> picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}

#### 9. dont-use-client-side
--> analyzed the javascript code used to validate password
==> picoCTF{no_clients_plz_7723ce}

#### 10. It is my Birthday
--> Birthday attack, submitted two files which has produces same hash i.e., hash collision (downloaded these files from the internet ) .This gave a flag
--> Files contents should be different , but hash should be same
==> picoCTF{c0ngr4ts_u_r_1nv1t3d_40d81ca2}

#### 11. Who are you?

#### 12. login
--> analyzed code in .js file for validation. The password was in code in base64 format, decoded it , got the flag.
==> picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}

#### 13. Includes
--> Found first of flag in .css file and second part of flag in .jss file.
==> picoCTF{1nclu51v17y_1of2_f7w_2of2_6edef411}

#### 14. Inspect HTML
--> View the page source
==> picoCTF{1n5p3t0r_0f_h7ml_1fd8425b}

#### 15. Local authority
--> The website takes input of username and password when submitted is redirected to login.php . In that the username and password are validated in client side only using javascript in .js file. username and password was hardcoded in .js file.
==> picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}

#### 16. Search source
--> Found the flag in .css file
==> picoCTF{1nsp3ti0n_0f_w3bpag3s_8de925a7}

#### 17. findme
--> the website had a form which on submitting username and password went to some redirection to other intermediate web pages before reaching a final web page. These intermediate redirections or reqeusts can be viewed in the burp proxy.
==> picoCTF{proxies_all_the_way_01e748db}

#### 18. MatchTheRegex
--> Website has regex pattern as " ^p.....F!? " in the comments in source page. Any input that matches the regular expression will give the flag
==> picoCTF{succ3ssfully_matchtheregex_f89ea585}

#### 19. WebGauntlet
--> sql injection
==> picoCTF{y0u_m4d3_1t_16f769e719ab9d3e310fd13dc1262ee1}

#### 20. WebGauntlet2
--> sql injection
==> picoCTF{0n3_m0r3_t1m3_fc0f841ee8e0d3e1f479f1a01a617ebb}

#### 21. SQL Direct
--> use postgresql database commands to view the contents in database.
==> picoCTF{L3arN_S0m3_5qL_t0d4Y_31fd14c0}

#### 22. WebGauntlet3
--> same as webgauntlet2
==> picoCTF{k3ep_1t_sh0rt_30593712914d76105748604617f4006a}

#### 23. Secrets
--> In the source page , the source of the image had a folder. visited the folder (i.e., if the source of the image is folder/image , then visit the /folder path ).(visited this recursively for multiple pages to get the flag)
==> picoCTF{succ3ss_@h3n1c@10n_51b260fe}

#### 24. Power Cookie
--> changed the value of admin cookie from 0 to 1
==> picoCTF{gr4d3_A_c00k13_65fd1e1a}

#### 25. Roboto Sana
--> Visited robots.txt . had an entry in base64 encoded , decoding it gave a path which had the flag value.
==> picoCTF{Who_D03sN7_L1k5_90B0T5_22ce1f22}

#### 26. Forbidden Paths
--> Given : website lives in /usr/share/nginx/html/ and the flag is at /flag.txt
--> the website sends a request to read a file in the current directory through the post request. we could modify the parameter to read the contents in previous directory using ../file.txt . Since we know the flag is at 4 directories up we can do ../../../../flag.txt to read the file
==> picoCTF{7h3_p47h_70_5ucc355_e5fe3d4d}

#### 27. picobrowser
--> send the request with user-agent as picobrowser to get the flag.
==> picoCTF{p1c0_s3cr3t_ag3nt_51414fa7}

#### 28. Irish-Name-Repo 1   (very interesting)
--> Found a login page , which gave error on giving ' , so got to know it was vulnerable to sql injection. tried basic auth bypass sql injection . Found flag
==> picoCTF{s0m3_SQL_fb3fe2ad}

#### 29. Irish-Name-Repo 2
--> same continued with enhanced filter security which blocked "OR" "UNION" keywords.
--> Used payload    admin' -- -
==> picoCTF{m0R3_SQL_plz_c34df170}

#### 30. More SQLi
--> used a basic auth sql injection bypass to bypass login screen 
--> then used union or order by to detect number of columns , then used union to detect the tables available in the sqlite database , then found a flag in one of the column in the database.
==> picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_62aa7500}
