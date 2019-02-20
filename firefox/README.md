# Firefox ESR 24 Docker Image

This Docker image provides web UI and VNC access for Firefox 24 ESR.

It is based on @jlesage `docker-baseimage-gui` image (https://github.com/jlesage/docker-baseimage-gui).

## Usage

```
docker run -p 5800:5800 rbschange/firefox:24-esr
```

Then open http://localhost:5800 and install the **RBS Change Manager** extension:

* `Outils` / `Modules complémentaires`
* Click on the "tools" icon topright, next to the search field and choose `Installer un module depuis un fichier`
* Choose `File system` on the left, and pick `rbs-change-manager.xpi` file at the end of the list
* Click `Open`, then `Installer maintenant` and then `Redémarrer maintenant`

You're all set!

