# Open a git repository in the Online Laboratory

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
    <label>Git repository host</label>
    <select id="repo-host" required>
        <option value="github">GitHub repository</option>
        <option value="gitlab">GitLab repository</option>
    </select>
    <br/><br/>
    <label>Repository owner (organisation / user) name</label>
    <input id="repo-org" type="text" required />
    <br/><br/>
    <label>Repository name</label>
    <input id="repo-name" type="text" required />
    <br/><br/>
    <label>Git ref (branch, tag, or commit)</label>
    <input id="repo-ref" type="text" value="HEAD" required />
    <br/><br/>
    <label>File to open (optional)</label>
    <input id="repo-path" type="text"/>
    <br/><br/>
    <label>Online Laboratory URL: <a id="repo-url" target="_blank"></a></label>
    <br/><br/>
    <label>Preview (using Jupyter nbviewer):</label>
    <iframe id="repo-preview" src="https://nbviewer.org/404.html" style="width: 100%; height: auto; aspect-ratio: 16 / 9;"></iframe>
</div>

<script>
  const lab_version = document.getElementById("lab-version");
  const repo_host = document.getElementById("repo-host");
  const repo_org = document.getElementById("repo-org");
  const repo_name = document.getElementById("repo-name");
  const repo_ref = document.getElementById("repo-ref");
  const repo_path = document.getElementById("repo-path");
  const repo_url = document.getElementById("repo-url");
  const repo_preview = document.getElementById("repo-preview");

  function updateRepoUrl() {
    if (repo_org.value && repo_name.value && repo_ref.value) {
      repo_url.href = `https://lab.climet.eu/${lab_version.value}/${repo_host.value}/${repo_org.value}/${repo_name.value}/${repo_ref.value}${repo_path.value ? '/' : ''}${repo_path.value}`;
      repo_url.style = "";
      repo_preview.src = `https://nbviewer.org/${repo_host.value}/${repo_org.value}/${repo_name.value}/tree/${repo_ref.value}/`;
    } else {
      repo_url.style = "color: grey;";
    }

    repo_url.innerText = `https://lab.climet.eu/${lab_version.value}/${repo_host.value}/${repo_org.value || "<org>"}/${repo_name.value || "<name>"}/${repo_ref.value || "<rev>"}${repo_path.value ? '/' : ''}${repo_path.value}`;

    if (repo_org.value && repo_name.value && repo_ref.value) {
      if (repo_path.value) {
        repo_preview.src = `https://nbviewer.org/${repo_host.value}/${repo_org.value}/${repo_name.value}/blob/${repo_ref.value}/${repo_path.value}`;
      } else {
        repo_preview.src = `https://nbviewer.org/${repo_host.value}/${repo_org.value}/${repo_name.value}/tree/${repo_ref.value}/`;
      }
    }
  }
  updateRepoUrl();

  lab_version.onchange = updateRepoUrl;
  repo_host.onchange = updateRepoUrl;
  repo_org.onchange = updateRepoUrl;
  repo_org.oninput = updateRepoUrl;
  repo_name.onchange = updateRepoUrl;
  repo_name.oninput = updateRepoUrl;
  repo_ref.onchange = updateRepoUrl;
  repo_ref.oninput = updateRepoUrl;
  repo_path.onchange = updateRepoUrl;
  repo_path.oninput = updateRepoUrl;
</script>
