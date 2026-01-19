# SiddhiEnterprise - Email Form Notifications

## Setup Instructions

### Step 1: Install Dependencies
```bash
npm install
```

### Step 2: Setup Gmail App Password

1. Enable 2-Factor Authentication on your Gmail account (if not already enabled)
2. Go to [Google Account Security](https://myaccount.google.com/security)
3. Scroll to "App passwords" section
4. Select "Mail" and "Windows Computer" (or your device)
5. Google will generate a 16-character app-specific password
6. Copy this password

### Step 3: Configure Environment Variables

1. Copy `.env.example` to `.env`
2. Fill in your Gmail credentials:
   ```
   GMAIL_EMAIL=karthikalkatte@gmail.com
   GMAIL_APP_PASSWORD=your_16_character_app_password
   ```

### Step 4: Deploy to Netlify

1. Push your code to GitHub
2. Connect your GitHub repo to Netlify
3. In Netlify Site Settings → Build & Deploy → Environment, add your environment variables
4. Deploy!

### Step 5: Test Email Submission

- Fill out the contact form on your website
- You should receive an email at **karthikalkatte@gmail.com** with the form details
- The form will show a success message

## How It Works

1. User submits the contact form on the website
2. JavaScript sends the form data to the Netlify Function
3. The Netlify Function (contact-notification.js) processes the request
4. Mailgun SMTP sends an email to karthikalkatte@gmail.com with the form details
5. User sees a success message

## Email Template

The email includes:
- Name
- Email (with reply-to set to sender's email)
- Message content
- Website branding

## Troubleshooting

- **"Missing email configuration"**: Check that GMAIL_EMAIL and GMAIL_APP_PASSWORD are set in Netlify environment variables
- **"Invalid login" error**: Make sure you're using the 16-character app password, not your regular Gmail password
- **2FA not enabled**: You must enable 2-Factor Authentication to create app passwords
- **Emails not received**: Check spam folder and verify Gmail credentials
- **Form shows error**: Check browser console for detailed error messages

## Production Notes

- Update `.gitignore` to include `.env` file
- Don't commit `.env` or app passwords to git
- App passwords are secure and only work with Gmail SMTP
- Each app password is unique and can be revoked anytime

