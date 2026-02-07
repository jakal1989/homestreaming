<html>
<body>
<!--StartFragment--><html><head></head><body><hr><h1>JellyPlex-Watched auf Synology</h1><p><strong>JellyPlex-Watched</strong> synchronisiert automatisch den „Watched“-Status von Medien zwischen <strong>Plex</strong> und <strong>Jellyfin</strong>, optimiert für den Einsatz auf einem <strong>Synology NAS</strong>.</p><hr><h2>Features</h2><ul><li><p>Automatische Synchronisation von „Watched“-Status zwischen Plex und Jellyfin</p></li><li><p>Unterstützt mehrere Benutzer</p></li><li><p>Läuft stabil als Docker-Container auf Synology DSM</p></li><li><p>Einfache Konfiguration über Umgebungsvariablen</p></li></ul><hr><h2>Voraussetzungen</h2><ul><li><p>Synology NAS mit <strong>Docker-Paket</strong></p></li><li><p>Plex Server mit <strong>Token</strong></p></li><li><p>Jellyfin Server mit Benutzerzugang</p></li></ul><hr><h2>Installation auf Synology</h2><h3>1. Docker Container erstellen</h3><ol><li><p>Öffne Docker auf deinem Synology NAS</p></li><li><p>Gehe zu <strong>Registry</strong> und suche nach:</p></li></ol><pre><code>luigi311/jellyplex-watched
</code></pre><ol start="3"><li><p>Lade das neueste Image herunter</p></li><li><p>Gehe zu <strong>Image → Starten</strong>, um einen neuen Container zu erstellen</p></li></ol><h3>2. Container konfigurieren</h3><ul><li><p><strong>Erweitert → Umgebungsvariablen</strong>:</p></li></ul>
<table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>Variable</th>
      <th>Wert</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>PLEX_BASEURL</td>
      <td>http://&lt;PLEX_SERVER_IP&gt;:32400/</td>
      <td>Plex Server URL</td>
    </tr>
    <tr>
      <td>PLEX_TOKEN</td>
      <td>&lt;PLEX_TOKEN&gt;</td>
      <td>Plex Token</td>
    </tr>
    <tr>
      <td>JELLYFIN_BASEURL</td>
      <td>http://&lt;JELLYFIN_SERVER_IP&gt;:8096/</td>
      <td>Jellyfin Server URL</td>
    </tr>
    <tr>
      <td>JELLYFIN_USER</td>
      <td>&lt;JELLYFIN_USER&gt;</td>
      <td>Jellyfin Benutzername</td>
    </tr>
    <tr>
      <td>JELLYFIN_PASSWORD</td>
      <td>&lt;JELLYFIN_PASSWORD&gt;</td>
      <td>Passwort</td>
    </tr>
  </tbody>
</table>

<ul><li><p><strong>Netzwerk</strong>: Bridge (Standard) oder dein NAS Netzwerk, je nach Plex/Jellyfin Zugriff</p></li></ul><h3>3. Container starten</h3><p>Nach der Konfiguration → <strong>Übernehmen → Starten</strong><br>Logs können im Docker UI unter <strong>Protokolle</strong> angezeigt werden</p><hr><h2>Troubleshooting</h2><ul><li><p>Prüfe die Netzwerkeinstellungen, wenn keine Synchronisation stattfindet</p></li><li><p>Stelle sicher, dass Plex Token korrekt ist</p></li><li><p>Jellyfin Benutzer muss Zugriff auf die Libraries haben</p></li></ul><hr><h2>Mitwirken</h2><p>Beiträge willkommen! Pull Requests oder Issues auf GitHub sind gern gesehen</p><hr><h2>Lizenz</h2><p>MIT-Lizenz</p><hr><p>Wenn du willst, kann ich jetzt noch eine <strong>GitHub-freundliche Version mit Badges und ein bisschen Style</strong> erstellen, die direkt professionell aussieht. Willst du, dass ich das mache?</p></body></html><!--EndFragment-->
</body>
</html>
