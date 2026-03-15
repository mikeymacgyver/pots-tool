# POTS Environmental Wellness Check — Hosting & Squarespace Setup

## Step 1: Host the tool (free options)

### Option A — GitHub Pages (recommended)
1. Create a free account at github.com
2. Create a new repository (e.g. `pots-tool`)
3. Upload `index.html` to the repo
4. Go to **Settings → Pages → Source → Deploy from branch → main**
5. Your URL will be: `https://YOUR-USERNAME.github.io/pots-tool/`

### Option B — Netlify Drop
1. Go to app.netlify.com/drop
2. Drag the `index.html` file onto the page
3. Netlify gives you a free URL instantly (e.g. `https://random-name.netlify.app`)
4. You can set a custom subdomain in Netlify settings

---

## Step 2: Embed in Squarespace

In your Squarespace page editor:

1. Add a **Code** block where you want the tool to appear
2. Paste the following embed code, replacing `YOUR_HOSTED_URL_HERE`:

```html
<iframe
  id="pots-tool"
  src="YOUR_HOSTED_URL_HERE"
  width="100%"
  height="720"
  frameborder="0"
  scrolling="no"
  title="POTS Environmental Wellness Check"
  style="border: none; border-radius: 16px; overflow: hidden;"
></iframe>

<script>
  // Auto-resize the iframe to fit content
  window.addEventListener('message', function(evt) {
    if (evt.data && evt.data.type === 'pots-resize') {
      var frame = document.getElementById('pots-tool');
      if (frame) frame.style.height = (evt.data.height + 24) + 'px';
    }
  });
</script>
```

> **Note:** The starting `height="720"` prevents a flash of short content while the page loads. The script auto-adjusts it after the user searches.

---

## APIs used (all free, no API key required)

| Data              | Source                          | Coverage   |
|-------------------|---------------------------------|------------|
| Weather           | Open-Meteo forecast API         | Global     |
| Barometric trend  | Open-Meteo hourly surface pressure | Global  |
| Air Quality (AQI) | Open-Meteo air quality API      | Global     |
| Pollen counts     | Open-Meteo CAMS pollen model    | Europe + partial North America |
| Geocoding         | Open-Meteo geocoding API        | Global     |

> Open-Meteo is open-source and free for non-commercial and research use. See open-meteo.com/en/terms for terms.

---

## Privacy & compliance notes

- **No data stored**: The tool is stateless. No user data, locations, or results are saved anywhere.
- **No cookies**: No tracking, analytics, or cookies of any kind.
- **AHPRA/APS compliance**: The tool is framed as an educational resource, not a clinical assessment. Disclaimers are displayed at both the top and bottom of the tool.
- **Australian Privacy Principles**: Because no personal or health information is collected, the tool does not trigger obligations under the Privacy Act 1988.
