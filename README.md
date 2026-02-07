<html>
<body>
<hr>
<h1>JellyPlex-Watched auf Synology</h1>
<p><strong>JellyPlex-Watched</strong> synchronisiert automatisch den „Watched“-Status von Medien zwischen <strong>Plex</strong> und <strong>Jellyfin</strong>, optimiert für den Einsatz auf einem <strong>Synology NAS</strong>.</p>
<hr>
<h2>Features</h2>
<ul>
  <li>Automatische Synchronisation von „Watched“-Status zwischen Plex und Jellyfin</li>
  <li>Unterstützt mehrere Benutzer</li>
  <li>Läuft stabil als Docker-Container auf Synology DSM</li>
  <li>Einfache Konfiguration über Umgebungsvariablen</li>
</ul>
<hr>
<h2>Voraussetzungen</h2>
<ul>
  <li>Synology NAS mit <strong>Docker-Paket</strong></li>
  <li>Plex Server mit <strong>Token</strong></li>
  <li>Jellyfin Server mit Benutzerzugang</li>
</ul>
<hr>
<h2>Installation auf Synology</h2>
<h3>1. Docker Container erstellen</h3>
<ol>
  <li>Öffne Docker auf deinem Synology NAS</li>
  <li>Gehe zu <strong>Registry</strong> und suche nach:<br><pre><code>luigi311/jellyplex-watched</code></pre></li>
  <li>Lade das neueste Image herunter</li>
  <li>Gehe zu <strong>Image → Starten</strong>, um einen neuen Container zu erstellen</li>
</ol>

<h3>2. Container konfigurieren</h3>
<p><strong>Erweitert → Umgebungsvariablen:</strong></p>
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
      <td>Passwort / API-Token</td>
    </tr>
  </tbody>
</table>
<ul>
  <li><strong>Netzwerk</strong>: Bridge (Standard) oder dein NAS Netzwerk, je nach Plex/Jellyfin Zugriff</li>
</ul>

<h3>3. Plex Token erhalten</h3>
<ol>
  <li>Öffne deinen Plex Server und gehe zu einer Medienbibliothek (z. B. Filme)</li>
  <li>Wähle einen Film aus → **drei Punkte → Medien-Info → XML-Datei anzeigen**</li>
  <li>In der URL nach folgendem Parameter suchen:<br>
  <code>X-Plex-Token=&lt;dein_plex_token&gt;</code></li>
  <li>Diesen Wert kopieren – das ist dein <strong>PLEX_TOKEN</strong></li>
</ol>

<h3>4. Jellyfin Token erhalten</h3>
<ol>
  <li>Lege einen Benutzer mit demselben Namen wie in Plex an (z. B. Plex-User heißt „John“, dann auch in Jellyfin „John“)</li>
  <li>Oben rechts auf das <strong>Personen-Icon → Übersicht → Benutzer → Plus-Logo</strong> klicken</li>
  <li>Benutzername wie in Plex eingeben, Passwort vergeben und Zugriff auf alle Bibliotheken zulassen</li>
  <li>Im nächsten Schritt „Server verwalten“ auswählen, nach unten scrollen und speichern</li>
  <li>Melde dich mit dem neuen Benutzerkonto an</li>
  <li>Gehe zu <strong>Einstellungen → API-Schlüssel</strong></li>
  <li><strong>Neuen API-Schlüssel erstellen</strong> und Namen vergeben</li>
  <li>Der generierte Wert ist dein <strong>JELLYFIN_PASSWORD</strong> / Token für die Docker-Umgebung</li>
</ol>

<h3>5. Container starten</h3>
<p>Nach der Konfiguration → <strong>Übernehmen → Starten</strong><br>
Logs können im Docker UI unter <strong>Protokolle</strong> angezeigt werden</p>

<hr>
<h2>Troubleshooting</h2>
<ul>
  <li>Prüfe die Netzwerkeinstellungen, wenn keine Synchronisation stattfindet</li>
  <li>Stelle sicher, dass Plex Token korrekt ist</li>
  <li>Jellyfin Benutzer muss Zugriff auf die Libraries haben</li>
</ul>

<hr>
<h2>Mitwirken</h2>
<p>Beiträge willkommen! Pull Requests oder Issues auf GitHub sind gern gesehen</p>

<hr>
<h2>Lizenz</h2>
<p>MIT-Lizenz</p>
</body>
</html>

