# Break the logic

Challenge-link: https://ch1.sbug.se/

# Solution

When we go to the website, it said that 'Aren't you ina wrong place!?'. That interesting right?

So i used gobuster to find another endpoints,

Command:
`gobuster -u "https://ch1.sbug.se/" -w directory-list-2.3-medium.txt` (**can also use dirb. dirb https://ch1.sbug.se/ **)

Output:
```/submit (Status: 200)
/admin (Status: 301)```

As, you can see there is interesting two endpoints called `/submit` and `/admin` endpoints.

So, if we look at the **/admin** endpoints, there is a admin login panel

I tried sql injections, but not work.

if you look at the cookie part from browser developer tool, there is a csrf token, hmm that interesting. 

So, if we look at the `/submit` endpoints, there is nothing in page, if you look at the source with (ctrl+u),

we can see the following comment 

```
<!--we heard that last commander used this key to forge a request:4JqorR6IXT4swdwN0qTPTwxtinom3AbZ5wNlEQjrPzEVJUUmDhVPFX21P3Xsnm04-->
```

So, as you saw in above, csrf token is interesing, so that can be admin's csrf token value.

So, i changed the csrf token's value with it(4JqorR6IXT4swdwN0qTPTwxtinom3AbZ5wNlEQjrPzEVJUUmDhVPFX21P3Xsnm04) and refresh the page(at /submit endpoint)

and got flag by viewing source

```
<!--keep this one private<br>-->
<!--SBCTF{L0g!cs_M@n_I_H@t3_7h3m}-->
```

# flag
SBCTF{L0g!cs_M@n_I_H@t3_7h3m}
