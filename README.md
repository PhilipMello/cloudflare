<img src="media/cloudflare-logo-512px.png" align="right">

![GitHub commit activity](https://img.shields.io/github/commit-activity/t/philipmello/cloudflare?style=for-the-badge&logo=github&logoSize=auto&labelColor=%238000ff&color=%23bf00ff)
![GitHub followers](https://img.shields.io/github/followers/philipmello?style=for-the-badge&labelColor=%2300bfff&color=%23bf00ff)
![GitHub forks](https://img.shields.io/github/forks/philipmello/cloudflare?style=for-the-badge&labelColor=%2300bfff&color=%23bf00ff)
![GitHub Repo stars](https://img.shields.io/github/stars/philipmello/cloudflare?style=for-the-badge&labelColor=%23bf00ff)
![GitHub watchers](https://img.shields.io/github/watchers/philipmello/cloudflare?style=for-the-badge&labelColor=%23bf00ff&link=https%3A%2F%2Fgithub.com%2FPhilipMello%2Fcloudflare%2Fwatchers)


# <p align="center">🔧 dnsflare</p>

# 📝 About
## Cloudflare DNS Script Automation

# 📚 Index
🔖 [Downloading and Installing](#-downloading-and-installing)<br>
🔖 [Navigating the tool](#-navigating-the-tool)<br>
🔖 [WordPress Rules](#-wordpress-rules)<br>

---
# 🔧 Downloading and Installing

```
wget https://raw.githubusercontent.com/PhilipMello/cloudflare/main/dnsflare && chmod +x dnsflare
```
OR
```
wget https://raw.githubusercontent.com/PhilipMello/cloudflare/main/dnsflare && chmod +x ktool && sudo mv dnsflare /usr/bin/
```

![Downloading and Installing](media/dnsflare.gif)

---
# 🔧 Navigating the tool

![Navigating the tool](media/navigating-the-tool.gif)

---

# 📊 WordPress Rules

## WAF

### > Firewall Rules
Go to: Website > Security > WAF > Firewall rules

## Block All Access to WP-ADMIN
| Firewall Rules | Expression |
:---------:|:------:
|Rule name (required)   |Block-All-Access-WP-ADMIN |
|Expression   |(http.request.full_uri eq "https://SITE-HERE.com/wp-login.php") or (http.request.uri.query eq "redirect_to=https%3A%2F%2FSITE-HERE.com%2Fwp-admin%2F&reauth=1") |
|Choose an action (Required)  |Block  |

## Rate Limit
### > Rate limiting rules
Go to: Website > Security > WAF > Tools

| Rate limiting rules | IP Access Rules |
:---------:|:------:
|Rule name (required)  |Rate-Limit-to-WP-LOGIN  |
|Expression     |(http.request.uri.path eq "/wp-login.php") |
|Requests (required) [3]|Period (required) [10 seconds]|
|Choose action      |Block |
|Place at |First|

## Allow Access for your iP to WP-ADMIN
### > Tools
Go to: Website > Security > WAF > Tools

| Tools | IP Access Rules |
:---------:|:------:
|Value   |YOUR-IPV4  |
|Value      |YOUR-IPV6  |