# MyDala Meditation

Generate meditations with voice, music and your style. A beautiful, feature-rich meditation web application with AI-powered meditation generation, freemium model, and Stripe integration.

## Features

### Core Features

1. **Authentication**
   - Email/password login and signup
   - Magic link authentication
   - Secure session management with Supabase Auth

2. **Create Meditation**
   - Duration selection: 5, 10, 15, 20, 30, 45, 60 minutes
   - Style options: Mindfulness, Zen-inspired, Tibetan-inspired (Shamatha-style), Tao-inspired, Non-dual awareness, Loving-kindness
   - Topic selection: Breath, Body scan, Awareness of awareness, Anxiety, Sleep, Compassion, Death contemplation
   - Voice settings: Language, accent, age, tone (stored as JSON)
   - Background music selector with preloaded tracks
   - Visual settings: Nature vs Mandala, kaleidoscope toggle, intensity slider

3. **Meditation Player**
   - Animated background with kaleidoscope effects using HTML5 Canvas
   - Audio playback controls (play, pause, restart)
   - Volume control
   - Progress bar
   - Display of meditation script
   - Full-screen immersive experience

4. **Freemium Model**
   - Free users: 5 AI meditations per month
   - Premium users: Unlimited AI meditations
   - Quota tracking with monthly reset
   - Upgrade modal when quota exceeded

5. **Subscription Management**
   - Stripe integration ready (requires Stripe configuration)
   - Premium plan at $9.99/month
   - Subscription status tracking
   - Customer portal access

6. **Affiliate Store**
   - Curated meditation products
   - Click tracking to database
   - External affiliate links
   - Product categories and images

7. **Dashboard**
   - Session statistics
   - Recent meditations
   - Quota usage display
   - Quick actions

## Tech Stack

- **Frontend**: Next.js 13 (App Router), TypeScript, Tailwind CSS
- **UI Components**: shadcn/ui, Radix UI
- **Backend**: Next.js API Routes
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Payments**: Stripe (ready to configure)
- **Deployment**: Netlify

## Database Schema

### Tables

1. **subscriptions** - User subscription data
2. **meditation_sessions** - Generated meditation sessions
3. **usage_quotas** - Monthly generation quota tracking
4. **affiliate_clicks** - Product click tracking
5. **background_tracks** - Audio tracks for meditation

All tables have Row Level Security (RLS) enabled for data protection.

## Getting Started

### Prerequisites

- Node.js 18+
- Supabase account
- Stripe account (for payments)

### Environment Variables

The following environment variables are already configured:

```
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

### Build

```bash
npm run build
```

## Project Structure

```
app/
├── api/
│   └── generate-meditation/  # Meditation generation endpoint
├── create/                    # Meditation creation page
├── dashboard/                 # User dashboard
├── login/                     # Login page
├── signup/                    # Signup page
├── player/[id]/              # Meditation player
├── pricing/                   # Pricing and upgrade page
└── shop/                     # Affiliate store

components/
├── navigation.tsx            # App navigation
└── ui/                       # shadcn/ui components

lib/
├── contexts/
│   └── auth-context.tsx     # Authentication context
├── supabase/
│   └── client.ts            # Supabase client
└── types/
    └── database.ts          # TypeScript types
```

## Features in Detail

### Meditation Generation

The app generates personalized meditation scripts based on:
- Selected duration, style, and topic
- User preferences for voice and visuals
- Background music selection

Scripts are stored in the database and can be replayed anytime.

### Kaleidoscope Effect

The player uses HTML5 Canvas to create mesmerizing kaleidoscope patterns that:
- Animate smoothly with configurable intensity
- Adapt to the selected visual type (nature or mandala)
- Can be toggled on/off per user preference

### Quota Management

Free users are limited to 5 AI-generated meditations per month:
- Quota resets automatically each month
- Usage tracked in the database
- Clear upgrade path to premium

### Affiliate Tracking

All product clicks are tracked with:
- User ID (if authenticated)
- Product details
- Timestamp
- User agent

This data can be used for analytics and conversion tracking.

## Security

- Row Level Security (RLS) enabled on all tables
- Users can only access their own data
- Authentication required for all protected routes
- Secure session management

## Disclaimer

**Important**: This app is designed for wellness and relaxation purposes only. It is not intended to diagnose, treat, cure, or prevent any medical condition. Users with mental or physical health concerns should consult qualified healthcare professionals.

## Stripe Integration

To enable premium subscriptions:

1. Set up a Stripe account
2. Create a product and pricing
3. Add Stripe API keys to environment variables
4. Implement webhook handlers for subscription events
5. Update pricing page with Stripe checkout

For detailed instructions, visit: https://bolt.new/setup/stripe

## Sample Data

The database includes sample background tracks:
- Ocean Waves (free)
- Forest Rain (free)
- Mountain Stream (free)
- Tibetan Bowls (premium)
- Crystal Chimes (premium)
- Zen Garden (free)

## Future Enhancements

- Real AI voice generation integration
- Audio file generation and storage
- Social sharing features
- Progress tracking and streaks
- Guided meditation courses
- Community features
- Mobile app versions

## License

Proprietary - All rights reserved
