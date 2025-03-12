# Moji Coin Telegram Bot

A Telegram bot for managing Moji Coin referral program with token rewards.

## Features

- User registration and profile management
- Referral link generation
- Token reward system
- Channel subscription verification
- Automatic reward distribution
- Profile completion system

## Requirements

- Node.js 18 or higher
- PostgreSQL database (via Supabase)
- Telegram Bot Token

## Environment Variables

Create a `.env` file with the following variables:

```env
TELEGRAM_BOT_TOKEN=your_bot_token
SUPABASE_URL=your_supabase_url
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_key
CHANNEL_1_ID=your_channel_1_id
CHANNEL_2_ID=your_channel_2_id
SAFEGUARD_LINK=your_safeguard_link
```

## Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Set up environment variables
4. Run the bot:
   ```bash
   npm start
   ```

## Deployment

### Railway.app (Recommended)

1. Fork this repository to your GitHub account
2. Create a new project on Railway.app
3. Connect your GitHub repository
4. Add environment variables in Railway dashboard
5. Deploy the application

### Alternative Deployment Options

- Render.com
- DigitalOcean
- Heroku

## Database Schema

The bot uses Supabase with the following schema:

```sql
CREATE TABLE users (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  telegram_id bigint UNIQUE NOT NULL,
  username text,
  tokens integer DEFAULT 0,
  referral_code text UNIQUE NOT NULL,
  referred_users integer DEFAULT 0,
  created_at timestamptz DEFAULT now(),
  name text,
  age integer,
  profile_completed boolean DEFAULT false
);
```

## Token Economics

- 1000 tokens = 5 USDT (after listing)
- 100 tokens awarded per successful referral