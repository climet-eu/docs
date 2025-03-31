# Open a file URL in the Online Laboratory

<div class="nice-form-group">
    <label>Online Laboratory version</label>
    <select id="lab-version" required>
        <option value="latest">Latest: v0.2.1</option>
        <optgroup label="v0.2">
            <option value="v0.2">v0.2: v0.2.1</option>
            <option value="v0.2.1">v0.2.1</option>
            <option value="v0.2.1">v0.2.0</option>
        </optgroup>
        <optgroup label="v0.1">
            <option value="v0.1">v0.1: v0.1.0</option>
            <option value="v0.1.0">v0.1.0</option>
        </optgroup>
    </select>
    <br/><br/>
    <label>File URL</label>
    <input id="https-file" type="url" required />
    <br/><br/>
    <label>Online Laboratory URL: <a id="https-url" target="_blank"></a></label>
</div>

<script>
  const lab_version = document.getElementById("lab-version");
  const https_file = document.getElementById("https-file");
  const https_url = document.getElementById("https-url");

  function updateHttpsUrl() {
    let https_file_url;
    try {
      https_file_url = new URL(https_file.value);
    } catch {}
    
    if (https_file_url) {
      https_url.href = `https://lab.climet.eu/${lab_version.value}/raw/https/${https_file.value.substring(https_file_url.protocol.length + 2)}`;
      https_url.style = "";
    } else {
      https_url.style = "color: grey;";
    }

    https_url.innerText = `https://lab.climet.eu/${lab_version.value}/raw/https/${https_file_url ? (https_file.value.substring(https_file_url.protocol.length + 2)) : "*<url>"}`;
  }
  updateHttpsUrl();

  lab_version.onchange = updateHttpsUrl;
  https_file.oninput = updateHttpsUrl;
  https_file.onchange = updateHttpsUrl;
</script>
