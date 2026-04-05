# Portfolio Website

## Project Goals
- Personal portfolio for a backend engineer
- Minimalist, static content (no interactivity)
- Blazing fast load times
- Cross-platform compatibility
- Clean, consistent aesthetics for reading

## Recommended Approach

### Tech Stack
- **Static site generator**: Astro (fastest, ships zero JS by default) or 11ty
- **Hosting**: Static hosting (Cloudflare Pages, Vercel, Netlify)
- **Styling**: Minimal CSS or Tailwind (lightweight)

### Key Commands (Astro example)
```bash
npm create astro@latest
npm run dev      # local dev
npm run build    # production build
npm run preview  # preview production build
```

### Performance Priorities
- Zero JavaScript shipped to client (use static SSG)
- Minimal external dependencies
- Optimized images (WebP/AVIF)
- Inline critical CSS
- Preload key resources

### Design Guidelines
- Typography-focused, excellent readability
- Dark/light theme support (system preference)
- Minimal animations, smooth page loads only
- High contrast text for accessibility

## File Structure
```
/src
  /pages      # routes
  /layouts   # page templates
  /components# reusable UI (minimal)
/public      # static assets
```

## Notes
- No dynamic content, comments, or user interaction
- Focus on static HTML delivery
- Test on mobile before deploy
