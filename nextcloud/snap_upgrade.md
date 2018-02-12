## Raspbian Nextcloud snap package maintenance:

- Make a [fresh backup](https://docs.nextcloud.com/server/12/admin_manual/maintenance/backup.html)

- Upgrade your Nextcloud snap, run command: `sudo snap refresh nextcloud`
- your Nextcloud server is immediately put into maintenance mode, refresh your Nextcloud page to see the maintenance screen mode
- To complete the upgrade run occ upgrade as your HTTP user. 
- Run command: `sudo -u www-data php occ upgrade`: command only for Debian/Ubuntu (Raspbian is based on Debian)
- Take your Nextcloud server out of maintenance mode.
- Re-enable third-party apps.
- It is best to update your Nextcloud installation with every new point release, and to never skip any major releases. 
- If upgrading via your Snap package manager fails, then you must perform a [Upgrade Manually](https://docs.nextcloud.com/server/12/admin_manual/maintenance/manual_upgrade.html) 
