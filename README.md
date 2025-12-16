# Lovers Moving - Booking Platform Setup Guide

Your website is ready for deployment! Follow these steps to go live with booking, CRM, and payments.

---

## 🚀 Step 1: Deploy to Vercel (5 minutes)

### Option A: Deploy via GitHub (Recommended)
1. Create a GitHub account at https://github.com if you don't have one
2. Create a new repository and upload all files from this folder
3. Go to https://vercel.com and sign up with GitHub
4. Click "Add New Project" → Import your GitHub repository
5. Click "Deploy" - that's it!

### Option B: Deploy via Vercel CLI
```bash
npm install -g vercel
cd lovers-moving-site
vercel
```

### Connect Your Custom Domain
1. In Vercel dashboard, go to your project → Settings → Domains
2. Add your domain (e.g., loversmoving.com)
3. Update your domain's DNS:
   - Recommended: Add a CNAME record pointing to `cname.vercel-dns.com`
   - Or follow Vercel's instructions in the dashboard for A record configuration

---

## 📅 Step 2: Set Up Cal.com Booking (10 minutes)

1. **Create Account**: Go to https://cal.com and sign up (free tier available)

2. **Create Event Type**:
   - Click "Event Types" → "New Event Type"
   - Name: "Consultation" (or "Transportation Consultation")
   - Duration: 30 minutes
   - Add custom questions for pickup/dropoff locations if desired

3. **Get Your Cal.com Username**: 
   - Your calendar link will be: `cal.com/YOUR_USERNAME/consultation`

4. **Update Your Website**:
   - Open `index.html`
   - Find and replace ALL instances of `YOUR_CAL_USERNAME` with your actual username
   - Example: Change `data-cal-link="YOUR_CAL_USERNAME/consultation"` to `data-cal-link="johnsmith/consultation"`

5. **Customize Appearance** (Optional):
   - In Cal.com: Settings → Appearance
   - Set brand color to `#E8E4DD` to match your site

---

## 📊 Step 3: Set Up HubSpot CRM (15 minutes)

### Create HubSpot Account
1. Go to https://app.hubspot.com/signup/crm
2. Sign up for the FREE CRM plan

### Get Your Portal ID
1. In HubSpot, click the gear icon (Settings)
2. Look in the URL - it contains your Portal ID: `app.hubspot.com/settings/PORTAL_ID/...`
3. Or go to Settings → Account Defaults → Account Info

### Create a Form for Lead Capture
1. Go to Marketing → Forms → Create Form
2. Choose "Embedded Form"
3. Add these fields (create custom properties as needed):
   - First Name (firstname)
   - Last Name (lastname)
   - Email (email)
   - Phone (phone)
   - Pickup Location (create custom: pickup_location)
   - Drop-off Location (create custom: dropoff_location)
   - Service Date (create custom: service_date)
   - Service Time (create custom: service_time)
   - Booking Type (create custom: booking_type)
4. Click "Publish" and get your Form GUID from the embed code

### Update Your Website
Open `index.html` and replace:
- `YOUR_HUBSPOT_ID` with your Portal ID (appears in tracking script)
- `YOUR_PORTAL_ID` with your Portal ID (appears in form submission URL)
- `YOUR_FORM_GUID` with your Form GUID

### Set Up Notifications
1. Go to Settings → Notifications
2. Enable email notifications for new form submissions
3. Create a workflow to auto-assign leads to team members

---

## 💳 Step 4: Set Up Stripe Payments (When Ready)

### Create Stripe Account
1. Go to https://dashboard.stripe.com/register
2. Complete business verification

### Create Payment Links or Products
**Option A - Simple Payment Links:**
1. Go to Payment Links in Stripe Dashboard
2. Create links for each service tier:
   - Single Day Service - $850
   - Weekly Package - $4,900
   - Monthly Tour - $19,500
   - 90-Day Package - $54,000
3. Add these links to your pricing table as "Book Now" buttons

**Option B - Embedded Checkout (Advanced):**
Add this to your site where you want a payment button:
```html
<script async src="https://js.stripe.com/v3/buy-button.js"></script>
<stripe-buy-button
  buy-button-id="YOUR_BUY_BUTTON_ID"
  publishable-key="YOUR_PUBLISHABLE_KEY"
></stripe-buy-button>
```

### Connect Stripe to HubSpot (Optional)
1. In HubSpot, go to App Marketplace
2. Search for "Stripe" and install the integration
3. This syncs payment data with customer records

---

## ✅ Quick Checklist

Before going live, make sure you've:

- [ ] Deployed to Vercel
- [ ] Connected your custom domain
- [ ] Created Cal.com account and event type
- [ ] Replaced `YOUR_CAL_USERNAME` in index.html (4 places)
- [ ] Created HubSpot account
- [ ] Created HubSpot form with custom fields
- [ ] Replaced `YOUR_HUBSPOT_ID` in index.html
- [ ] Replaced `YOUR_PORTAL_ID` in index.html
- [ ] Replaced `YOUR_FORM_GUID` in index.html
- [ ] Tested the booking flow end-to-end
- [ ] Set up email notifications in HubSpot

---

## 🔧 File Structure

```
lovers-moving-site/
├── index.html      # Main website with all integrations
├── vercel.json     # Vercel deployment configuration
└── README.md       # This setup guide
```

---

## 📞 Support Resources

- **Vercel Docs**: https://vercel.com/docs
- **Cal.com Docs**: https://cal.com/docs
- **HubSpot Academy**: https://academy.hubspot.com
- **Stripe Docs**: https://stripe.com/docs

---

## 🎯 Next Steps After Launch

1. **Set up Google Analytics** for traffic tracking
2. **Create automated email sequences** in HubSpot for lead nurturing
3. **Add testimonials** from satisfied clients
4. **Set up review collection** via Google Business Profile
5. **Consider adding live chat** (HubSpot has a free option)

Good luck with your launch! 🚀
