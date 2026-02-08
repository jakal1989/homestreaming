<html>
<body>
<hr>
<h1>JellyPlex-Watched on Synology</h1>
<p><strong>JellyPlex-Watched</strong> automatically synchronizes the “Watched” status of media between <strong>Plex</strong> and <strong>Jellyfin</strong>, optimized for use on a <strong>Synology NAS</strong>.</p>
<hr>
<h2>Features</h2>
<ul>
  <li>Automatic synchronization of “Watched” status between Plex and Jellyfin</li>
  <li>Supports multiple users</li>
  <li>Runs reliably as a Docker container on Synology DSM</li>
  <li>Easy configuration via environment variables</li>
</ul>
<hr>
<h2>Requirements</h2>
<ul>
  <li>Synology NAS with <strong>Container Manager</strong></li>
  <li>Plex Server with <strong>token</strong></li>
  <li>Jellyfin Server with user access</li>
</ul>
<hr>
<h2>Installation on Synology</h2>
<h3>1. Create Docker Container</h3>
<ol>
  <li>Open Container Manger on your Synology NAS</li>
  <li>Go to <strong>Registry</strong> and search for:<br><pre><code>luigi311/jellyplex-watched</code></pre></li>
  <li>Download the latest image</li>
  <li>Go to <strong>Project → create</strong> to create a new container project</li>
</ol>

<h3>2. Configure Container project</h3>
<ol>
  <li>Project name: First, set a project name such as <strong>"JellyPlexWatched"</strong>.</li>
  <li>Path: Create or set a folder path, for example <strong>/docker/Jellyplex</strong>.</li>
  <li>Source: Select <strong>docker-compose.yml</strong> and either upload the compose file or create a new <strong>docker-compose.yml</strong> and copy &amp; paste the compose content.</li>
  <li>Adjust the variable values according to your setup and preferences.</li>
</ol>
<table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>Variable</th>
      <th>Value</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>PLEX_BASEURL</td>
      <td>http://&lt;PLEX_SERVER_IP&gt;:32400</td>
      <td>Plex server URL</td>
    </tr>
    <tr>
      <td>PLEX_USERS</td>
      <td>&lt;PLEX_USER&gt;</td>
      <td>Plex username</td>
    </tr>
    <tr>
      <td>PLEX_TOKEN</td>
      <td>&lt;PLEX_TOKEN&gt;</td>
      <td>Plex token</td>
    </tr>
    <tr>
      <td>JELLYFIN_BASEURL</td>
      <td>http://&lt;JELLYFIN_SERVER_IP&gt;:8096</td>
      <td>Jellyfin server URL</td>
    </tr>
    <tr>
      <td>JELLYFIN_USERS</td>
      <td>&lt;JELLYFIN_USER&gt;</td>
      <td>Jellyfin username</td>
    </tr>
    <tr>
      <td>JELLYFIN_PASSWORD</td>
      <td>&lt;JELLYFIN_PASSWORD&gt;</td>
      <td>Password / API token</td>
    </tr>
    <tr>
      <td>SYNC_FROM_PLEX_TO_JELLYFIN</td>
      <td>True/False</td>
      <td>Sync from Plex to Jellyfin</td>
    </tr>
    <tr>
      <td>SYNC_FROM_JELLYFIN_TO_PLEX</td>
      <td>True/False</td>
      <td>Sync from Jellyfin to Plex</td>
    </tr>
  </tbody>
</table>
<ul>
  <li><strong>Network</strong>: Bridge (default) or your NAS network, depending on Plex/Jellyfin access</li>
</ul>

<h3>3. Get Plex Token</h3>
<ol>
  <li>Open your Plex Server and go to a media library (e.g. Movies)</li>
  <li>Select a movie → <strong>three dots → Media Info → View XML</strong></li>
  <li>Look in the URL for the following parameter:<br>
  <code>X-Plex-Token=&lt;your_plex_token&gt;</code></li>
  <li>Copy this value – this is your <strong>PLEX_TOKEN</strong></li>
</ol>

<h3>4. Get Jellyfin Token</h3>
<ol>
  <li>Create a user with the same name as in Plex (e.g. Plex user “John” → Jellyfin user “John”)</li>
  <li>Click the <strong>user icon (top right) → Dashboard → Users → plus icon</strong></li>
  <li>Enter the same username as Plex, set a password, and allow access to all libraries</li>
  <li>In the next step, select “Manage server”, scroll down, and save</li>
  <li>Log in with the new user account</li>
  <li>Go to <strong>Settings → API Keys</strong></li>
  <li><strong>Create a new API key</strong> and assign a name</li>
  <li>The generated value is your <strong>JELLYFIN_PASSWORD</strong> / token for the Docker environment</li>
</ol>

<h3>5. Start Container</h3>
<p>After configuration → <strong>Apply → Start</strong><br>
Logs can be viewed in the Container Manager UI under <strong>Container/JellyPlexWatched/Logs</strong></p>

<hr>
<h2>Troubleshooting</h2>
<ul>
  <li>Check network settings if synchronization does not work</li>
  <li>Make sure the Plex token is correct</li>
  <li>The Jellyfin user must have access to the libraries</li>
</ul>

<hr>
<h2>Contributing</h2>
<p>Contributions are welcome! Pull requests or issues on GitHub are appreciated</p>

<hr>
<h2>License</h2>
<p>MIT License</p>
</body>
</html>
