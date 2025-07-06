# *seo*

**Search Engine google :**
Search Engine google work in two way one with crawler and two with algorithm

---

**crawler :**
follow the exist link in website and collect info in link and save that info in database and next algorithm check info and verifies the obtained information and ...

**point one :** if you want google crawler see your website faster you must give your domain to a high traffic website in this way crawler can find you faster 

**onpage** = the thing you put to your site that user see

**ofpage** = is a your link that exist in other website  

**point two :** every time you visit a web page one crawle visit that page with you to see what you do in that page and how mush you stay

***

### key words

**key words :** the word or sentence that user search in google(like tag in website)

##### tool for find word key in google :
+ [wordtracker](https://www.wordtracker.com/)
+ [keyworddiscovery](https://www.keyworddiscovery.com/)
+ [adsgoogle](https://ads.google.com/)

**point one :** search for searched word in google is very important to know what user search to find what his/her want

you must prioritize your key word and after that you must show your key words to your customer if your customer confirmed that key words you can use in your prioritization 

+ if you want to know how many site used (searched word) in their site put your searched word in "" in search google like:

```
"teach java script"
```

+ if you want to know how many site work on (searched word) in their site use allintitle:"search word" like :
```
allintitle:"teach java script"
```

**point two :** the best place to put your word key is in title and h1

***

### Structure main page

**point one :** design main page must be simple to user can find every thing that want

**point two :** load speed page is very important

**tag title :** every page must have unique title and max character must be 64 and min title sentence must be 3 part
```html
<title>teach javascript program</title>
```

#### meta tag

**meta Description :** this meta explains your page max character must be between 160 
to 300 char
```html
<meta name="Description" content="explains">
```

**meta keyword :** this meta became Obsolete and you can i put your keyword in this meta 
```html
<meta name="keywords" content="javascript,teach javascript,what is javascript">
```

**meta canonical :** this meta make google robot understand that which one is main url address and don't index another url
```html
<meta name="canonical" href="https://diesella.ir">
```

#### h1 to h6 tag
**tag h1 :** your page must have one h1, max and min h1 must be one and h1 content and title content must be different if content became the same this make The importance of the page decreases

**h2 :** don't use very much h2 in page

**h3 to h6 :** use freely

#### a tag
**a :** is better to be same content a and href and google say link short is better then big href and is better to use short link goo.gl and use attribute title in a , this attribute explain about this link

#### img tag
**img :** for google is important to use attribute alt and title for img tag , alt show explain about your image if your image doesn't show

#### content writing
**content writing :** must be simple and use image and video in your content to make your content more interesting

#### important page

**in nav you must have :**
* one part for Products
* one part for blog
* one part for services
* one part for contact-us
* one part for about-us
* one part for questions

**contact-us :** is better to put your email and phone and address to Increase customer trust and after send customer email you must send answer for that email

**about-us :** you must write about your site and in the end, agin you must put your email and phone and address in the content

#### post page
* content don't be Repetitious
* use image and video in content
* content must be interesting and br true
* content has h tag and img and video has alt and title

---

### tools:

**woorank**
this tools for analyze your website and suggest to make your seo site better and you can use once of day

**checkpagerank**
[checkpagerank](https://checkpagerank.net) : is a page that give you your page rank

---

#### favorite link in seo :

google know when you make a questions how search every title seo to answer your questions so you can search that questions and put to your title in your content post and put that questions in ht tag but **don't overdo it**

---

#### make link:
create link in same content has more effect and also, the older this link is, the more effective it is.

---
#### Links that are not valid:
* attribute rel has nofollow
* attribute target has _blank
---

### url
don't use persian word in url

---
### back link

* the url back link that you pub in web content must has related content to content web
* the web that you put your back link in it's content must has good rating
* back link must doesn't have **rel = "nofollow"**

---
### page rank
page rank is a score that google gives to your page and your score computing of your link to your page and your rank page is between 0 to 10

### Link Exchange
we can exchange link in dual or triple.
dual : is mean you have two site that share each other link in their site
triple : is mean we have three site that A share link to B and B share to C and C share to A
and if this link being in content it make link Higher value

---
### Page Authority
Page Authority is a score that google give you from 0 to 100

site:{address your site} => for see how many link google indexed  

---
#### onPage :
seo in inside of site is mean in program

**domain site :** what is a good domain extension? what is your competition?
* .com : for com abbreviation of companies and For commercial work
* .net : for network
* .co : for companies

#### offPage :
seo outside of site

---

#### who.is
don't lock whois and write your ownership domain

**important point :** 
---



#### Improved loading speed

##### tools : 
**[gtmetrix](https://gtmetrix.com/) :**   
analyze seo site 

---

#### robots.txt

```
user-agents: * <!-- All crawlers ... -->
allow: / <!-- ... are allowed to see all sites -->
sitemap: https://diesella.ir/sitemap.xml <!-- address sitemap -->

user-agents: *
Disallow: /project-file/  <!-- robots doesn't allow to index project-file -->

user-agents: Googlebot-Image <!-- robot googlebot don't allowed to ... -->
Disallow: /Images/logo.png <!-- ... index logo.png -->

user-agents: *
Disallow: /*.gif$ <!-- robots doesn't allowed to index files.gid -->
```

### meta tag
``` html
<meta name="robots" content="nofollow,noindex">  <!-- robots don't follow links and don't index this page -->
```
**point one :** Separate the title field and the h1 field.

**meta description :** There is a brief explanation for the page. put word between 160 to 300 characters
```html
<meta name="description" content="">
```

**meta canonical :** You specify the main address of the page.
```html
<meta name="canonical" content="https://toplean.com">
```
**attribute alt :** put word between 16 to 50 characters it's better to max be 16 characters
```html
<img sec="" alt="">
```

### search analytics

* click: how many clicked
* impressions: how many show in search google
* ctr (click to rate): Shows average impressions and clicks.
* position: show where is in search google 1.2 ( 1:page one 2:The second option)

---

### links
**External links :** other site that link to your site
* Top linked pages: top the links that other make for you
* Top linking sites: the sites that make a link for you
* Top linking text: the text that set in anchor like `<a>text</a>`

**Internal links :** the links that you make in your site

---

### Manual actions
if your site is identified as spam. google will tell you what happened and how to fix it.

---

### Structure data 
 * schema.org : example for Structure schema

 ---

 ### Demographic details
 Reporting for user age and gender

 ---

 ### Campaigns url builder
for create promotional links