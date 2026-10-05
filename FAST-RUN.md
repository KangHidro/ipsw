## Fast run: Download and Decrypt DMG on Ubuntu
- Use Ubuntu or WSL Ubuntu, intsall this ipsw tool: `sudo snap install ipsw`
- If you use WSL Ubuntu, files located in `\\wsl.localhost\Ubuntu\home`
- Check yor device code, E.g `iPhone17,5`
- Download current lastest IPSW: `ipsw download ipsw --device iPhone17,5 --latest` or beta IPSWW (you need login with Dev Account): `ipsw dl dev -u <your email> -p <your password>`
- Extract File System (fs) DMG: `ipsw extract --dmg fs iPhone17,5..._Restore.ipsw`
- Copy the decryption key (base64 string) for a specific `DMG.AEA` file after run: `ipsw fw aea --key ./23G83__iPhone17,5/24A5408d__iPhone17,5/094-95657-089.dmg.aea`
- Decrypt AEA: `ipsw fw aea --key-val "base64:2IInR...." ./23G83__iPhone17,5/094-95657-089.dmg.aea --output ./23G83__iPhone17,5/`
- Open decrypted DMG by 7z

### Create and Install IPCC
- Open decrypted DMG by 7z
- Open `System → Library → Carrier Bundles`
- Find your carrier and extract it, Eg. `Viettel_vn.bundle`
- Create `Payload` folder, put `Viettel_vn.bundle` inside. Notice: Only 1 carrier bundle at the same time.
- Send `Payload` to zip
- Rename `Payload.zip` to `Payload.ipcc`
- Install (via 3uTool or your tool)
- I use iTunes:
- - Enable carrier-testin: `"%ProgramFiles%\iTunes\iTunes.exe" /setPrefInt carrier-testing 1`
  - Connect iPhone by cable
  - Open iTunes, click `iPhone` icon (near top-left)
  - Hold `Shift` + Click `Check for Update`
  - In type box, select IPCC file type
  - Select IPCC file
  - Wait for install
  - On iPhone, go to About to check carrier version
  - If it install successfully, restart iPhone
