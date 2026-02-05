# Image Optimization Guide

Your site now has **native lazy loading** implemented, but for maximum performance gains, you should also optimize the actual image files.

## What's Already Done ✅

1. **Lazy Loading**: First 3 images load immediately (`loading="eager"`), rest load as you scroll (`loading="lazy"`)
2. **sitemap.xml**: All 41 artworks indexed for Google Image Search
3. **robots.txt**: Search engines can crawl your site
4. **SEO Image Tags**: Every image has descriptive alt text

## Next Steps for Image Optimization

### Option 1: Manual (Recommended for Control)

**Tools:**
- **Squoosh.app** (free, web-based, no sign-up)
- **ImageOptim** (Mac) or **TinyPNG** (web)

**Process:**
1. Go to squoosh.app
2. Upload each image
3. Convert to WebP format
4. Adjust quality to 80-85% (reduces file size by 50-80%)
5. Download optimized version
6. Replace original files

**Before/After Example:**
- `IMG_6231.jpg` - Original: 2.5MB → WebP: 450KB (82% smaller!)

### Option 2: Batch Processing (Fastest)

**Using ImageMagick (command line):**
```bash
# Convert all JPGs to WebP
for img in art/*.jpg art/old/*.jpg; do
    cwebp -q 85 "$img" -o "${img%.jpg}.webp"
done

# Convert PNG
cwebp -q 85 art/IMG_6246.png -o art/IMG_6246.webp
```

**Then update HTML:**
```html
<!-- Old -->
<img src="art/IMG_6231.jpg">

<!-- New -->
<img src="art/IMG_6231.webp">
```

### Option 3: Use GitHub Actions (Automated)

Create `.github/workflows/optimize-images.yml` to automatically compress on commit.

## WebP Browser Support

✅ Chrome, Firefox, Safari, Edge all support WebP
✅ Can provide JPG fallback if needed (but not necessary in 2026)

## Expected Performance Gains

- **Load time**: 3-5 seconds → 1-2 seconds
- **Bandwidth**: 100MB → 20-30MB
- **Mobile experience**: Much faster
- **SEO**: Better rankings (Google rewards fast sites)
- **User experience**: Smoother scrolling

## Priority Order

1. **Convert to WebP** (biggest impact)
2. **Resize images** (if any are >2000px wide, resize to 1500px max)
3. **Remove metadata** (EXIF data adds unnecessary weight)

All images are already lazy loading, so this is just about file size now!
