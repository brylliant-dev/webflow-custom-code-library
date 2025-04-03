# Webflow Custom Code Library for Brylliant Devs

---
## Code for animating CMS collection:

> Update class name based on how you named the collection item.

`CSS:`
```html
<style>
    .expert-team-collection-item {
        opacity: 0;
        transition: opacity 1s ease-in-out;
    }
    .expert-team-collection-item.animate {
        opacity: 1;
    }
</style>

```

`JS:`
```html
<script>
    $(document).ready(function () {
        // Select CMS items
        const cmsItems = $(".expert-team-collection-item").get()
        // Create the observer
        let observer = new IntersectionObserver(
            (entries) => {
            entries.forEach((entry, index) => {
                if (entry.isIntersecting) {
                setTimeout(() => {
                    // Add class to animate the item
                    $(entry.target).addClass("animate")
                }, 150 * index) // Stagger delay, adjust as needed
                observer.unobserve(entry.target)
                }
            })
            },
            { threshold: 0.25 },
        ) // Adjust threshold as needed
        // Observe each CMS item
        cmsItems.forEach((item) => {
            observer.observe(item)
        })
    })
</script>
```

---
## Code for Calendly Script:
```html
<!-- Calendly Head Code -->
<link
  href="https://assets.calendly.com/assets/external/widget.css"
  rel="stylesheet"
/>

<!-- Calendly Footer Code -->
<script
  src="https://assets.calendly.com/assets/external/widget.js"
  type="text/javascript"
  async=""
></script>
<script>
  $(".calendly").click(function () {
    Calendly.initPopupWidget({
      url: "https://calendly.com/brylliantsolutions/first-call?hide_gdpr_banner=1",
    })
    return false
  })

  $(".menu-overlay").click(function () {
    $(".text-size-14b.close").click()
  })
</script>
```

---
## Code for Year Script:
```html
<!-- Footer Year Script-->
<script>
  var d = new Date()
  var n = d.getFullYear()
  $(".year").text(n)
</script>
```
