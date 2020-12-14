# GOUPIL WORKLOAD OVERVIEW

## Collaboration
### Additional meetings
- Precise design specs
- Validate content
- Precise extra functionalities
- Feedback iterations

### Training
- Basic CMS usage
- Blog post creation
- Search Engine Optimization
- Social media management
- Newsletter / Campaigns
- Web shop (catalogue / order processing)

## Support
- software updates
- inrastructure monitoring

## Visual & content
### Overall design
- Typography
- Colors
- Page layout (mobile / tablet / laptop)
### Individual pages
- Home page
- Default content pages (e.g. "Association", "Education" etc.)
- HFS page
- Contact page
- Events page
- Tutorials page (adherants only)
- Shop pages: storefront, category views, detail views
- Newsletter default email templates

### Content creation
- Clarify initial page / menu structure
- Write text for each page
- Edit graphic elements (icons etc.)
- Select photos
- Scrape existing content from the current site that needs to be preserved or archived
    - Identify which part(s) of the site are to be kept
    - Write the spiders / web-crawlers scripts
    - Export texts / visuals in coherent data structures

## Development

### HTML / CSS / templates
- All designs need to be "reproduced" on the browser
- Navigation menu(s)

### User management (mostly out-of-the-box, slight customizations):
- User management system 
- User roles / permissions i.e. admins, authors, volunteers (mostly out-of-the-box, slight customizations)
- GDPR compliance ( users must be able to view / download / delete any of their own data  we keep )

### CMS customization (mostly out-of-the-box, slight customizations):
- custom toolbar buttons and plugins for (even) easier content creation
- unit tests

### Blog application (mostly out-of-the-box)
- Configuration
- Templates customization / styles to match design

### Email back-end for outbound emails:
- Integration with an email delivery app (e.g. sendinblue, sendgrid etc.) This ensures emails are not blocked nor end up in the spam folder.
- unit tests

### SEO optimization
- template work
- django-page-meta configuration

### Cookie-consent-management
- Cookiebot integration (https://www.cookiebot.com/fr/)

### Shop
- Snipcart intagration (https://snipcart.com/) 
- Product / product categories models and templates
- Payment gateway
- unit tests
Disclaimer: snipcart will charge 1.5% of your sales if your sales are over 500€/month

### Adherants
- Integration with helloasso API (we need to know whether a user has adhered via helloasso)
- unit tests
https://dev.helloasso.com/v3/responses#paiements

### Intranet
- Adaptation to User roles/permissions
- File organisation utils (custom upload locations, folder creation etc.)
- Potential external storage integration (e.g. AWS S3)
- unit tests

### Social-media management
- page-meta attributes
- auto-publish blog posts on fb, instagram via their graph-APIs
- unit tests

### Video tutorials
- restricted pages url config (for adherants only - else redirect to "become adherant page")
- Choose video-hosting platform (e.g. YouTube, DailyMotion, Vimeo) create Goupil account
- integrate via CMS plugin
- unit tests

### Newsletter
- Maintain subscribers' mailing list(s)
- 2-way synch with external API for mail-delivery / marketing service
- task definition (span big campaigns over several days not to exceed 300 emails per day limit)
- unit tests

### Events
- event model
- enable filtering (by event_type or by users permissions)
- Interactive map integration (https://leafletjs.com/)
- Calendar
- Potential intranet integration (recurrent events / scheduling)
- unit tests

### Counter plugin
show a counter of hours-of-work / number-of-animals for any given day
- model, view, tempates
- unit tests


## Migration & infrastructure
- switch cloud infrastructure (within OVH or other)
- DNS changes ("transfer" domain name to new site)
- email solution (for setting up @goupilconnection.org mailboxes)
    - setup required accounts
    - potentially migrate existing email archives (hope not)
- schedule database backups


## Technical details
For the tech savvy here is a list of the proposed stack:

**Docker** is used for containerizing the application (https://www.docker.com/)

### Services
- Back-end:
    - language: python (https://www.python.org/)
    - framework: django (https://www.djangoproject.com/)
    - Content Management System: djangoCMS (https://www.django-cms.org/en/)
- Database: Postgresql (https://www.postgresql.org/)
- Caching / message broker: Redis (https://redis.io/)
- Task queue / scheduler: Celery (https://docs.celeryproject.org/en/stable/)
- Search engine: elastisearch (https://www.elastic.co/elastic-stack)

### Devops
- version control: git (https://git-scm.com/)
- duplicated staging and live server environments
- automated pipelines for testing & continuous integration / deployment: via github actions (https://github.com/)
- automated software updates via dependabot (https://dependabot.com/)
- log monitoring via sentry (https://sentry.io)


## Estimated annual operational costs

- Cloud hosting: ~5€ / month => ~60€ / year
- Domain name costs: ~ 10 / year
- Cookiebot: free until 500 pages, then 9€ / month
- email hosting : depends on number of mailboxes: for 3 mailboxes: 15€ / year
- email delivery service: free for 300 emails/day (this is for emails sent FROM the web application)

**Overall : ~ 85€ - 100€ year**
