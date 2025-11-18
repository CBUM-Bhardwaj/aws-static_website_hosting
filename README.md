# AWS — Static Website Hosting on S3  
*Simple project, but packed with real understanding.*

---

## 1. Project Overview

**Goal:** Host a static website (HTML, CSS, JS) on **Amazon S3**, and understand how S3, permissions, and IAM actually work behind the scenes.

This project teaches:

- *What* S3 static hosting really is  
- *Why* cloud/DevOps engineers must know it  
- *How* to set it up safely  
- *When* S3 hosting is the right choice  
- *Who* needs access (and why IAM matters)

This is your AWS “hello world”, but with real logic behind every step.

---

## 2. Why This Project Matters (WHY)

Let’s keep it real:  
If you can’t host a basic site on S3, you’re not ready for Cloud or DevOps roles.  
Because this one tiny project touches many things you will use everywhere in AWS.

Think about it:

- S3 = storage  
- IAM = who can do what  
- Policies = permissions on resources  
- Public access settings = security  
- Website endpoint = how AWS serves content  

This isn’t a “fun project”.  
It’s literally the **entry point** to actual AWS understanding.

### **Real-life use cases**
Companies use S3 static hosting for all kinds of things:

- Product landing pages  
- Company documentation  
- Internal tools  
- Status pages  
- Portfolios  
- Frontend builds from React / Angular  

This is not theory — this exists everywhere.

### **Why it helps your mindset**
Once you do this properly, you stop thinking:

> “AWS is complicated.”

and start thinking:

> “AWS is just logic and permissions.”

This project flips that switch.

---

## 3. What Is Static Website Hosting on S3? (WHAT)

Let’s break it down without jargon.

### A static website is just:
- HTML  
- CSS  
- JS  
- Images  

No backend.  
No database.  
No logic happening on the server.

A static site = files.

That’s it.

### Amazon S3 is:
Basically a giant online folder (“bucket”) where you store files.

### So what does S3 static hosting do?
It tells S3:

> “Bro, don’t treat this bucket like simple storage.  
> Behave like a mini web server, serve my files as a website.”

After you enable it:

- S3 gives you a **website URL**  
- You decide the **index** file (typically `index.html`)  
- You decide the **error** file  
- Anyone on the Internet can load your website (if permissions allow)

**In simple words:**  
Upload your website → flip one switch → it becomes a live website.

---

## 4. When Should You Use S3 Static Hosting? (WHEN)

### **Use it when your site is simple**
Examples:
- Portfolio  
- Blog  
- Documentation  
- A small frontend project  
- A landing page  

### **Why use it?**
Because it’s:
- Cheap (almost free)  
- Very fast  
- No maintenance  
- Zero servers required  
- Extremely reliable  

### **Don’t use S3 if you need backend stuff**
If your website needs:
- Login system  
- User accounts  
- Payments  
- Server-side generated pages  
- Real-time chat  
- Database connectivity  

S3 cannot handle that.

Then you need a combo like:

- S3 (frontend)  
- API Gateway (API routing)  
- Lambda (backend logic)  
- DynamoDB/RDS (database)  

### **Simple rule to remember**
If your website is just files → S3 works.  
If your website needs “thinking” → S3 doesn’t.

---

## 5. Architecture of This Project

Here’s the simplest possible cloud architecture:

User → Internet → S3 Website Endpoint → Your Website Files


### Components (very simple, but each has a purpose):

#### **1. S3 Bucket**
Stores the website files.

#### **2. Bucket Policy**
This decides:
- who can access files  
- what actions they can do  

For a website, we allow:
- Everyone can **read** files  
- Nobody can **write** or **delete**

#### **3. Static Website Hosting**
Turns your bucket into a public-facing website.

#### **4. (Optional Later) CloudFront + Route 53**
If you want:
- HTTPS (SSL)  
- Custom domain (`www.yoursite.com`)  
- CDN caching  

But for this Level 1, S3 alone is enough.

---

## 6. Prerequisites

- AWS account  
- Basic idea of regions (ex: Mumbai = ap-south-1)  
- A small website folder with at least:

`index.html`  
(Optional) `error.html`

### Example `index.html`  
Just to get started:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>S3 Static Site</title>
  </head>
  <body>
    <h1>Hello from Amazon S3!</h1>
    <p>This static website is hosted using S3.</p>
  </body>
</html>
