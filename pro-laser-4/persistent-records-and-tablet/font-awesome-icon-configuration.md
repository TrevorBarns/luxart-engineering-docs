---
description: >-
  Instructions on configuring Font Awesome to prevent icons from not being shown
  on Lidar Records Tablet.
icon: font-awesome
---

# Font Awesome Icon Configuration

### What is Font Awesome?

Font Awesome is a web font and icon provider which allows developers to easily implement intuitive icons into their website.

### Why would I want to proceed with this configuration?

To restore the Lidar Records Tablet icons. Font Awesome offers both paid and free plans. However, free plans are limited by the number of page views and since this is a free resource I will not be paying for page views beyond what the free plan offers.&#x20;

This can result in icons disappearing as my plan's page views exceed the limit. The following steps will help you configure ProLaser4 to use your own account which will reduce the odds of this occurring and help you fix the issue should it occur in the future.

### How to configure Font Awesome & Pro Laser 4

1. Create an account on Font Awesome: [https://fontawesome.com/start](https://fontawesome.com/start)
2. Navigate to "Your Kits": [https://fontawesome.com/kits](https://fontawesome.com/kits)
3. Click "Create Your First Kit": [https://fontawesome.com/kits/new](https://fontawesome.com/kits/new)
4. Select the "Free Styles" icon kits.\
   ![](<../../.gitbook/assets/image (1).png>)
5. Select Next.
6. Select "Hosted by Us".
7. You do not need to provide a domain, select Next.
8. Enter a name for the kit.
9. Select "Make My Kit".
10. Copy the unique kit token provided on the next page. \
    ![](<../../.gitbook/assets/image (2).png>)
11. Open `ProLaser4\UI\html\index.html`
12. Paste the unique code overriding the default on line 13.\
    ![](<../../.gitbook/assets/image (3).png>)
13. Restart ProLaser4.

\
After following these steps you should have icons in your Lidar Records Tablet, you may need to refresh this token based on how large your server is, and how many "page views" your server uses.\
