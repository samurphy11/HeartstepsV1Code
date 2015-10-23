# HeartSteps pilot data analysis

- [Mounting M+Box](#mouting-mbox)
- [Exporting data](#exporting-data)
- [Preparing data for analysis](#preparing-data-for-analysis)
- [Running data summaries](#running-data-summaries)

## Mounting M+Box

Connect to M+Box via [WebDAV](http://community.box.com/t5/Managing-Your-Content/Does-Box-support-WebDAV/ta-p/310) using the following steps. This allows you to access your M+Box folders as though they were part of your local filesystem.

1. From your [M+Box account settings](https://umich.app.box.com/settings/account), set up an external password. You will use this password and your primary M+Box email address (also found in settings) as the credentials to mount access M+Box content.
2. Follow the system-specific instructions below.

### Mac

### Windows

#### Windows 8/8.1/10

- Open File Explorer, from either the Start Menu (Windows 10) or the Taskbar. Click "This PC" (This will likely be listed in "Frequent Folders", but if not, find it in the sidebar).
- Click "Map Network Drive" in the Ribbon at the top of the window. If you do not see this, click the "Computer" tab next to the blue File button.
- From the "Drive" dropdown menu, choose `Z:\`.
- In "Folder", enter `https://dav.box.com/dav`
- Check the "Connect using different credentials" box, then click Finish.
- Enter your U-M email address and the external password you created in your M+Box account settings, and click OK.

You may need to close and reopen File Explorer for the new drive to appear.

#### Windows 7


- Click Start, then Computer.
- Click "Map network drive" towards the top of the window.
- From the "Drive" dropdown menu, choose `Z:\`.
- In "Folder", enter `https://dav.box.com/dav`
- Check the "Connect using different credentials" box, then click Finish.
- Enter your U-M email address and the external password you created in your M+Box account settings, and click OK.

You may need to close and reopen File Explorer for the new drive to appear.


### Ubuntu

- Install [davfs2](http://savannah.nongnu.org/projects/davfs2) and create a mount point called `mbox` in your home directory with the following terminal commands. Here `USERNAME` should be replaced with your own system login name.
```shell
sudo sed -ir 's/^# use_locks(.+)1$/# use_locks\10/g' /etc/davfs2/davfs2.conf
sudo dpkg-reconfigure davfs2
sudo usermod -a -G davfs2 USERNAME
mkdir ~/mbox
echo "https://dav.box.com/dav /home/USERNAME/mbox davfs rw,user,noauto 0 0" | sudo tee -a /etc/fstab
chmod 600 /home/USERNAME/.davfs2/secrets
```
- Logout and log back in.
- M+Box can now be mounted with the command `mount ~/mbox`.

## Exporting data

### Jawbone and Google Fit

Download using the browser interface at <http://jitai-api.appspot.com>.

### HeartSteps

Ensure your system has [M+Box mounted](#mounting-mbox) and the following software installed.

- [Google App Engine Python SDK](https://cloud.google.com/appengine/downloads)
- [Python 2.7+](https://www.python.org/downloads/)

From the command line, navigate to the `heartstepsdata/exporter` folder in your local copy of this repository. Run the export script specific to your system. When prompted, enter the HeartSteps GAE account credentials.

## Preparing data for analysis

## Running data summaries
