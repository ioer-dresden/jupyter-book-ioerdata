
# 🏆 My Achievements

Welcome to your **Urban Data Investigator Badge Gallery**!

Every completed mission earns you a badge. Follow your progress, celebrate your achievements, and unlock new skills as you explore ioerDATA.

```{raw} html
<div id="badge-gallery"></div>

<script>
(function () {
  const gallery = document.getElementById("badge-gallery");

  // Badge names for all eight missions
  const badges = [
    "Data Collector",
    "Mission 2 Badge",
    "Mission 3 Badge",
    "Mission 4 Badge",
    "Mission 5 Badge",
    "Mission 6 Badge",
    "Mission 7 Badge",
    "Mission 8 Badge"
  ];

  // Read saved mission progress
  function renderGallery() {
    const completed = badges.filter((_, i) =>
      localStorage.getItem(
        `urban_data_mission_${i + 1}_completed`
      ) === "true"
    ).length;

    // Display progress bar and badge cards
    gallery.innerHTML = `
      <h3>🎯 Your Progress: ${completed} / 8 Missions</h3>

      <div style="background:#e0e0e0;border-radius:8px;
                  height:14px;overflow:hidden;margin-bottom:24px;">
        <div style="background:#70a401;
                    width:${completed / 8 * 100}%;
                    height:100%;"></div>
      </div>

      <div style="display:grid;
                  grid-template-columns:repeat(auto-fit,minmax(170px,1fr));
                  gap:16px;">

        ${badges.map((name, i) => {
          const n = i + 1;

          const earned = localStorage.getItem(
            `urban_data_mission_${n}_completed`
          ) === "true";

          const date = localStorage.getItem(
            `urban_data_mission_${n}_completed_at`
          );

          const badge = localStorage.getItem(
            `urban_data_badge_${n}`
          ) || name;

          return `
            <div style="border:1px solid #ddd;border-radius:12px;
                        padding:20px;text-align:center;
                        background:${earned ? "#f1f8e9" : "#f5f5f5"};
                        opacity:${earned ? "1" : "0.65"};">

              <div style="font-size:40px;">
                ${earned ? "🏅" : "🔒"}
              </div>

              <h4>Mission ${n}</h4>

              <p><strong>${earned ? badge : "Badge Locked"}</strong></p>

              <p>${earned ? "✅ Badge Earned" : "Not yet earned"}</p>

              ${earned && date
                ? `<small>Completed: ${new Date(date).toLocaleDateString()}</small>`
                : ""}
            </div>
          `;
        }).join("")}
      </div>

      ${completed === 8
        ? "<h3>🎉 Congratulations! All 8 missions completed!</h3>"
        : "<p>🚀 Continue your investigation to unlock more badges!</p>"}
    `;
  }

  renderGallery();
  window.addEventListener("pageshow", renderGallery);
})();
</script>
```
