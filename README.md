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

---
## Code for Manipulating Webflow's background video start time:
```html
<script>
  $(document).ready(function(){
    var video = $('video'); //target class 
    if(video.length){
      video.get(0).pause();
      setTimeout(function(){ //remove the delay if needed
        if(window.innerWidth < 768){//only works on tablet below
          video.get(0).currentTime = 4;
        }
        video.get(0).play();
      }, 9000);
    }
  });
</script>
```

---
## Resetting interaction in Finsweet
```html
<script>
    /**reset IX**/
    var Webflow = Webflow || []
    Webflow.push(function () {
      $("html").attr("fs-cmstabs-resetix", "64cb3cf628252df1fd7ef0fc")
      window.Webflow && window.Webflow.destroy()
      window.Webflow && window.Webflow.ready()
      window.Webflow && window.Webflow.require("ix2").init()
      document.dispatchEvent(new Event("readystatechange"))
    })
    /**close resetIX**/
</script>
```
