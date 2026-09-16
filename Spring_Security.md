**Common Attacks:**

1. CSRF:
![img_10.png](images/img_10.png)

- a link tricks user to click and redirect to a site where you are already authenticated like gmail.
Example:
![img_11.png](images/img_11.png)

![img_12.png](images/img_12.png)

Browser automatically adds the session in the cookie.

How to get protected from CSRF token:

![img_13.png](images/img_13.png)

![img_14.png](images/img_14.png)

**2. XSS Cross-Site Scripting:**
![img_15.png](images/img_15.png)

Example: A page where user can add comment.
- Get endpoit to get all comments from DB
- POST endpoint to add a new comment.
- Attack happens by inserting malicious code as comment that can deform a website.

![img_16.png](images/img_16.png)

![img_17.png](images/img_17.png)

How to Prevent this attack:

![img_18.png](images/img_18.png)

3. CORS 

![img_19.png](images/img_19.png)

![img_20.png](images/img_20.png)

4. SQL Injection:

![img_21.png](images/img_21.png)

![img_22.png](images/img_22.png)

How to prevent:

![img_23.png](images/img_23.png)

**Spring Security 1:**

![img_24.png](images/img_24.png)

Architecure:

![img_25.png](images/img_25.png)

There are multiple security filters
For each authentication method there are different filters.

![img_26.png](images/img_26.png)

AuthenticationManager ----> ProviderManager -----> AuthenticationProvider





