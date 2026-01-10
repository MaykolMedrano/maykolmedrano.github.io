# Image Optimization Guide

## Critical Images to Optimize

### **URGENT - img_2.gif (4.9MB)**
This GIF is killing your performance. You need to convert it to video format:

```bash
# Install ffmpeg first, then run:
ffmpeg -i projects/img_2.gif -movflags faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" projects/img_2.mp4

# For WebM (better compression):
ffmpeg -i projects/img_2.gif -c:v libvpx-vp9 -b:v 0 -crf 30 projects/img_2.webm
```

**Expected reduction: 4.9MB → ~500KB (90% smaller)**

### **HIGH PRIORITY - profile.png (377KB → 800x800)**
```bash
# Create optimized WebP version:
# Install ImageMagick or use online tool: squoosh.app

# Resize to actual display size and convert to WebP:
magick profile.png -resize 320x320 -quality 85 profile.webp

# Create AVIF (even better compression):
magick profile.png -resize 320x320 -quality 80 profile.avif
```

**Expected reduction: 377KB → ~30KB WebP (92% smaller)**

### **img_3.png (568KB)**
```bash
magick projects/img_3.png -quality 85 projects/img_3.webp
magick projects/img_3.png -quality 80 projects/img_3.avif
```

**Expected reduction: 568KB → ~60KB WebP (89% smaller)**

## Implementation Steps

1. **Generate optimized versions** using the commands above
2. **Update references** in your .qmd files to use modern formats with fallbacks
3. **Add lazy loading** to images below the fold
4. **Verify** the site still works correctly

## Tools You Can Use

- **Squoosh.app** - Browser-based, no installation needed
- **ImageMagick** - Command line tool
- **FFmpeg** - For GIF → Video conversion
- **Online converters** - cloudconvert.com, convertio.co

## After Optimization

Run Lighthouse again to see the performance improvements. You should see:
- LCP improvement: 40-60%
- Overall performance score: +20-30 points
- Mobile experience: Much faster loading
