# Open a gist in the Online Laboratory

<div class="nice-form-group">
    <label>Online Laboratory version</label>
    <select id="lab-version" required>
        <option value="latest">Latest: v0.3.0</option>
        <optgroup label="v0.3">
            <option value="v0.3">v0.3: v0.3.0</option>
            <option value="v0.3.0">v0.3.0</option>
        </optgroup>
        <optgroup label="v0.2">
            <option value="v0.2">v0.2: v0.2.1</option>
            <option value="v0.2.1">v0.2.1</option>
            <option value="v0.2.0">v0.2.0</option>
        </optgroup>
        <optgroup label="v0.1">
            <option value="v0.1">v0.1: v0.1.0</option>
            <option value="v0.1.0">v0.1.0</option>
        </optgroup>
        <option value="main">Development: main</option>
    </select>
    <br/><br/>
    <label>Gist host</label>
    <select id="gist-host" required>
        <option value="github">GitHub Gist</option>
    </select>
    <br/><br/>
    <label>Gist owner (organisation / user) name</label>
    <input id="gist-org" type="text" required />
    <br/><br/>
    <label>Gist ID</label>
    <input id="gist-id" type="text" required />
    <br/><br/>
    <label>File to open</label>
    <input id="gist-path" type="text" required />
    <br/><br/>
    <label>Online Laboratory URL: <a id="gist-url" target="_blank"></a></label>
    <br/><br/>
    <label>Preview (using Jupyter nbviewer):</label>
    <iframe id="gist-preview" src="https://nbviewer.org/404.html" style="width: 100%; height: auto; aspect-ratio: 16 / 9;"></iframe>
</div>

<script>
  const lab_version = document.getElementById("lab-version");
  const gist_host = document.getElementById("gist-host");
  const gist_org = document.getElementById("gist-org");
  const gist_id = document.getElementById("gist-id");
  const gist_path = document.getElementById("gist-path");
  const gist_url = document.getElementById("gist-url");
  const gist_preview = document.getElementById("gist-preview");

  const searchParams = new URLSearchParams(window.location.search);
  gist_org.value = searchParams.get("org");
  gist_id.value = searchParams.get("id");
  gist_path.value = searchParams.get("path");

  function updateGistUrl() {
    if (gist_org.value && gist_id.value && gist_path.value) {
      gist_url.href = `https://lab.climet.eu/${lab_version.value}/gist/${gist_host.value}/${gist_org.value}/${gist_id.value}/${gist_path.value}`;
      gist_url.style = "";
    } else {
      gist_url.style = "color: grey;";
    }

    gist_url.innerText = `https://lab.climet.eu/${lab_version.value}/gist/${gist_host.value}/${gist_org.value || "<org>"}/${gist_id.value || "<id>"}/${gist_path.value || "<filepath>"}`;

    if (gist_org.value && gist_id.value) {
      gist_preview.src = `https://nbviewer.org/gist/${gist_org.value}/${gist_id.value}${gist_path.value ? '/' : ''}${gist_path.value}`;
    }
  }
  updateGistUrl();

  lab_version.onchange = updateGistUrl;
  gist_host.onchange = updateGistUrl;
  gist_org.onchange = updateGistUrl;
  gist_org.oninput = updateGistUrl;
  gist_id.onchange = updateGistUrl;
  gist_id.oninput = updateGistUrl;
  gist_path.onchange = updateGistUrl;
  gist_path.oninput = updateGistUrl;
</script>
