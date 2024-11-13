# Setting Up SSL for GitHub Pages with a .web.id Custom Domain

To enable SSL for your GitHub Pages site with a `.web.id` custom domain, follow these steps.

## 1. Configure Your Domain on GitHub Pages
1. Go to your repository on GitHub.
2. Navigate to **Settings** > **Pages**.
3. In the **Custom Domain** section, enter your `.web.id` domain (e.g., `yourdomain.web.id`) and save.
4. Check the **Enforce HTTPS** option if it’s available (you may need to wait for DNS changes to propagate first).

## 2. Set Up DNS Records on Your Domain Registrar
Log in to your domain registrar where you registered your `.web.id` domain, and set the following DNS records:

### Required DNS Records

|    Name   |   Type   |  TTL  |               RDATA                |
|:---------:|:--------:|:-----:|------------------------------------|
|     @     |    A     | 3600  | 185.199.108.153                    |
|     @     |    A     | 3600  | 185.199.109.153                    |
|     @     |    A     | 3600  | 185.199.110.153                    |
|     @     |    A     | 3600  | 185.199.111.153                    |
|    www    |  CNAME   | 3600  | `<your-github-username>.github.io` |


**Explanation:**
- **Name**: Use `@` to represent your root domain (`yourdomain.web.id`). Use `www` if you also want `www.yourdomain.web.id` to point to your GitHub Pages.
- **Type**: `A` for root domain IPs; `CNAME` for subdomain redirection.
- **TTL**: Time-to-live in seconds (3600 is a standard choice, though it can be adjusted).
- **RDATA**: For `A` records, use GitHub’s IP addresses. For `CNAME`, use your GitHub username's default GitHub Pages domain.

After setting these records, it may take up to 24-48 hours for DNS changes to propagate.

## 3. Verify SSL
Once DNS changes are in effect, return to GitHub Pages settings, refresh, and check the **Enforce HTTPS** option if it's now clickable. GitHub will provision the SSL certificate automatically, and your `.web.id` domain will be accessible via HTTPS.

After this, your site should be live with SSL encryption, ensuring a secure connection for visitors.

## Contributor
mukhamadazistholib278[at]gmail[dot]com