# Open a git repository in the Online Laboratory

<div class="nice-form-group">
    <label>Quick entry: GitHub Repository URL</label>
    <input id="repo-quick" type="url" />
    <br/><br/>
    <label>Online Laboratory URL: <a id="repo-url-top" target="_blank"></a></label>
    <br/><br/>
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
        <option value="main">Development: main</option>
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
    <label>Online Laboratory URL: <a id="repo-url-bottom" target="_blank"></a></label>
    <br/><br/>
    <label>Preview (using Jupyter nbviewer):</label>
    <iframe id="repo-preview" src="https://nbviewer.org/404.html" style="width: 100%; height: auto; aspect-ratio: 16 / 9;"></iframe>
</div>

<script>
  const repo_quick = document.getElementById("repo-quick");
  const lab_version = document.getElementById("lab-version");
  const repo_host = document.getElementById("repo-host");
  const repo_org = document.getElementById("repo-org");
  const repo_name = document.getElementById("repo-name");
  const repo_ref = document.getElementById("repo-ref");
  const repo_path = document.getElementById("repo-path");
  const repo_urls = [document.getElementById("repo-url-top"), document.getElementById("repo-url-bottom")];
  const repo_preview = document.getElementById("repo-preview");

  function updateQuickUrl() {
    const url = parseGithubUrl(repo_quick.value);

    if (!url) {
      repo_quick.style = "";
    }

    if (!url.owner || !url.name) {
      repo_quick.style = "border-bottom-color: var(--nf-invalid-input-border-bottom-color);";
      return;
    }

    if (url.host === "github.com") {
      repo_host.value = "github";
    } else {
      repo_quick.style = "border-bottom-color: var(--nf-invalid-input-border-bottom-color);";
      return;
    }

    repo_org.value = url.owner;
    repo_name.value = url.name;
    repo_ref.value = url.branch || "HEAD";
    repo_path.value = url.filepath;

    repo_quick.style = "border-bottom-color: var(--nf-valid-input-border-bottom-color);";

    updateRepoUrl();
  }

  repo_quick.onchange = updateQuickUrl;
  repo_quick.oninput = updateQuickUrl;

  function updateRepoUrl() {
    for (const repo_url of repo_urls) {
      if (repo_org.value && repo_name.value && repo_ref.value) {
        repo_url.href = `https://lab.climet.eu/${lab_version.value}/${repo_host.value}/${repo_org.value}/${repo_name.value}/${repo_ref.value}${repo_path.value ? '/' : ''}${repo_path.value}`;
        repo_url.style = "";
        repo_preview.src = `https://nbviewer.org/${repo_host.value}/${repo_org.value}/${repo_name.value}/tree/${repo_ref.value}/`;
      } else {
        repo_url.style = "color: grey;";
      }

      repo_url.innerText = `https://lab.climet.eu/${lab_version.value}/${repo_host.value}/${repo_org.value || "<org>"}/${repo_name.value || "<name>"}/${repo_ref.value || "<rev>"}${repo_path.value ? '/' : ''}${repo_path.value}`;
    }

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
