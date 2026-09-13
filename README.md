# Ma configuration Debian/Ubuntu

Script d'automatisation pour configurer et mettre à jour mes systèmes Debian et Ubuntu.

> [!NOTE]
> Ce script est conçu exclusivement pour **Debian** et **Ubuntu Desktop** avec l'environnement de bureau **GNOME**.

---

## 🧪 Versions testées
* Debian 13 (trixie)
* Ubuntu 26.04 LTS

---

## 🔍 Ce que fait le script

- Configure le gestionnaire de paquets APT et applique les mises à jour
- Configure le gestionnaire de paquets Flatpak et applique les mises à jour
- Configure le gestionnaire de paquets Snap et applique les mises à jour
- Propose de redémarrer le système si nécessaire
- Configure les dépôts officiels et additionnels au système
- Supprime les Snaps forcés par Ubuntu
- Ajoute ou supprime les paquets deb dont ceux spécifiés dans `packages.list`
- Ajoute ou supprime les paquets flatpak spécifiés dans `flatpak.list`
- Ajoute ou supprime les paquets snap spécifiés dans `snap.list`
- Personnalise la configuration du système
- Propose de redémarrer le système si nécessaire

---

## 📁 Structure

```bash
.
├── assets/             # Ressources copiées sur le système (si existantes)
├── config.sh           # Script principal
├── flatpak.list        # Liste des paquets Flatpak à installer/désinstaller
├── packages.list       # Liste des paquets Deb à installer/désinstaller
└── snap.list           # Liste des paquets Snap à installer/désinstaller
```

---

## 🚀 Usage

### 1. Configuration de Flatpak (Optionnel)
Par défaut, le script installe et gère le système de paquets Flatpak. Pour désactiver Flatpak, ouvrez le fichier `config.sh` et modifiez la variable suivante :
```bash
IS_FLATPAK_ENABLED="false"
```

> [!IMPORTANT]
> A faire avant le premier lancement du script sinon le système Flatpak sera installé !

### 2. Exécution du script
Ouvrez votre terminal dans le dossier du dépôt, autorisez l'exécution du script et lancez-le avec les privilèges super-utilisateur (root) :
```bash
chmod +x config.sh
sudo ./config.sh
```

### 3. Mode vérification de mises à jour
Il est possible de faire uniquement une vérification des mises à jour (listing des paquets deb, snap et flatpak à mettre à jour sans appliquer de modifications) via l'option `check` :
```bash
sudo ./config.sh check
```

### 4. Utilisation pour la maintenance
Ce script est idempotent. Vous pouvez l'exécuter plusieurs fois de suite; les étapes déjà configurées seront simplement ignorées. De fait, le script peut être utilisé pour :
* **Configuration initiale** du système après une installation fraîche
* **Mise à jour** de la configuration et des listes de paquets
* **Mise à jour globale** de tous les paquets du système

---

## 🙏 Crédits

Ce script est inspiré du [travail initial](https://github.com/aaaaadrien/fedora-config) d'Adrien de [linuxtricks.fr](https://www.linuxtricks.fr)