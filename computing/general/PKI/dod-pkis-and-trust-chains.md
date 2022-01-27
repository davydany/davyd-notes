# Finding DoD's Trust Chain Certificates

If you've worked with DoD clients long enough, like I have, at some 
point you will be trying to setup your computer to trust DoD sites.
To do this, you will need to setup your computer to trust certificates
issued by DoD's Root and Intermediate Certificates.

If you want an overview of how the PKI Infrastructure works, please
checkout my other article [How Trust Works in Computing](./how-trust-works-in-computing.md).

So to trust the DoD's Root and Intermediate Certificates, you need
to get the DoD's Root and Intermediate Certificate Authorities' 
Certificates, and put them on your Computer, and tell your computer
to trust certificates issued and signed with theses Certificate 
Authorities' certificates.

## Warning

The following steps get the certificates from official DoD sites. 
Please do not get certificates from other sites as they might have
not been signed by the DoD, and you might be trusting nefarious 
Certificate Authorities.

## Setting up on Windows

So, for Windows, the DoD offers a simple tool that you simply download
and install on your Windows Machine, and you're on your merry way.

1. Visit the PKI/PKE document Library: https://public.cyber.mil/pki-pke/pkipke-document-library/
2. Scroll to Page 5 (or so), and look for a file that says something 
similar to **InstallRoot <version> NIPR <arch>-but Windows Installer**
  - Here, **<version>** would be the latest version
  - Here, **<arch>** would be either 32 or 64
  - At the time of this writing the following versions are available:
    - InstallRoot 5.5 NIPR 32-bit Windows Installer 
    - InstallRoot 5.5 NIPR 64-bit Windows Installer 
    - InstallRoot 5.5 NIPR Non-Administrator 32-bit Windows Installer 
3. Download the version that is appropriate to the system you are using
4. Once downloaded, please open the installer and install it on your machine
5. Once installed, open **InstallRoot** by going to your **Start** menu and searching for it
6. Under **Microsoft Local Computer**, and under 
**Install DoD Certificates**, select all the certificates that apply,
and then on the top, click on **Install Certificates**.

## Setting up on Mac OS X

1. Visit the PKI/PKE document Library: https://public.cyber.mil/pki-pke/pkipke-document-library/
2. Scroll to Page 2 (or so), and look for a file that says something similar to **DoD Approved External PKI Trust Certificate Chains**. 
3. There might be multiple versions, so please select the highest number that corresponds to the latest updated date.
4. Once downloaded, please extract the ZIP file
5. Inside the extracted directory, go to `_DoD/Trust_Anchors_Self-Signed`
6. Now, open the **KeyChain Access** app on your Mac
7. Make sure that on the left, the **login** keychain is selected.
8. Drag and drop each of the `.cer` file that is under **Trust_anchors_Self-Signed**
9. Once it has been imported, double-click on the appropriate DoD Root Certificate
10. In the dialog that opens up, select the section called **> Trust**
11. For the section **When using this certificate:**, select **Always Trust**
12. Close the window, and you might be propted for password or your finger print. Please authenticate yourself here so the action is completed.
13. Repeat this for all the Root Certificates that you imported

