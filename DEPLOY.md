# EDGE Calgary - Deploy to GitHub Pages
# Domain: edgecalgary.org (registered Namecheap, Order 198545870, Mar 31 2026)

## 1. Create GitHub repo
- Go to github.com (innov8ideas4u-alt account)
- New repo: edge-site
- Public, no README

## 2. Push from local
```
cd D:\Dev\edge
git init
git add .
git commit -m "Initial EDGE site"
git remote add origin https://github.com/innov8ideas4u-alt/edge-site.git
git push -u origin main
```

## 3. Enable GitHub Pages
- Repo → Settings → Pages
- Source: Deploy from branch → main → / (root)
- Save — site live at: innov8ideas4u-alt.github.io/edge-site

## 4. Point Namecheap DNS to GitHub Pages
Namecheap → Domain List → edgecalgary.org → Manage → Advanced DNS
Delete any existing A records, then add:
```
Type    Host    Value               TTL
A       @       185.199.108.153     Auto
A       @       185.199.109.153     Auto
A       @       185.199.110.153     Auto
A       @       185.199.111.153     Auto
CNAME   www     innov8ideas4u-alt.github.io.  Auto
```

## 5. Set custom domain in GitHub
- Repo → Settings → Pages → Custom domain
- Enter: edgecalgary.org
- Check "Enforce HTTPS" (may take up to 24hrs for SSL cert)

## 6. Add CNAME file to repo
Create file: D:\Dev\edge\CNAME (no extension) containing only:
edgecalgary.org

Then:
```
git add CNAME
git commit -m "Add custom domain"
git push
```

## 7. Upload promo video to YouTube
- Upload D:\Dev\Projects\edge-promo\out\EdgePromo.mp4
- Set visibility: Unlisted
- Copy the video ID from the URL (youtube.com/watch?v=XXXXXXXXX)

## 8. Add video section to index.html
Paste before </main>:

<section style="text-align:center; margin-bottom:4rem; padding:0 2rem;">
  <h2>See EDGE in Action</h2>
  <div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;max-width:800px;margin:1rem auto;">
    <iframe style="position:absolute;top:0;left:0;width:100%;height:100%;"
      src="https://www.youtube.com/embed/YOUR_VIDEO_ID"
      frameborder="0" allowfullscreen>
    </iframe>
  </div>
</section>

## Final Result
- edgecalgary.org → live site with SSL (free)
- Video embedded from YouTube (free)
- Hosted on GitHub Pages (free)
- Total annual cost: $7.48
