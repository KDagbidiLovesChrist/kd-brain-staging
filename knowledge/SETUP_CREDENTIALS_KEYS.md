# CREDENTIALS AND KEYS SETUP
**Local key and credential generation (no network operations, no cloud sync)**

---

## MASTER ENCRYPTION KEY

**Purpose**: Generate encryption master key for file protection.

**Create directories:**
```powershell
New-Item -ItemType Directory -Path "D:\encryption" -Force
New-Item -ItemType Directory -Path "D:\Backups\encryption" -Force
```

**Download libsodium.js:**
- Official source: https://github.com/jedisct1/libsodium.js/releases
- Download latest: libsodium.js-X.X.X.tar.gz
- Extract to: `C:\tools\libsodium-js\`

**Create key generation script:**

**File: `C:\scripts\generate_master_key.js`**
```javascript
const libsodium = require('C:\\tools\\libsodium-js\\libsodium.js');
const fs = require('fs');

libsodium.ready.then(() => {
  const masterKey = libsodium.randombytes(libsodium.crypto_secretbox_KEYBYTES);
  const keyHex = Buffer.from(masterKey).toString('hex');
  
  const keyPath = 'D:\\encryption\\master.key';
  fs.writeFileSync(keyPath, keyHex);
  fs.chmodSync(keyPath, 0o400);
  
  console.log('Master key created: ' + keyPath);
  
  const backupPath = 'D:\\Backups\\encryption\\master.key.backup';
  fs.writeFileSync(backupPath, keyHex);
  fs.chmodSync(backupPath, 0o400);
  
  console.log('Backup created: ' + backupPath);
});
```

**Run locally:**
```powershell
node C:\scripts\generate_master_key.js
```

**Verify:**
```powershell
Get-Item D:\encryption\master.key
Get-Item D:\Backups\encryption\master.key.backup
```

---

## SSH KEY FOR REMOTE AUTHENTICATION

**Create SSH directory:**
```powershell
if (-not (Test-Path $env:USERPROFILE\.ssh)) {
  New-Item -ItemType Directory -Path $env:USERPROFILE\.ssh
}
```

**Generate key:**
```powershell
ssh-keygen -t ed25519 -f $env:USERPROFILE\.ssh\id_ed25519 -N ""
```

Creates:
- `~/.ssh/id_ed25519` (PRIVATE, keep local)
- `~/.ssh/id_ed25519.pub` (PUBLIC, share with friend)

**Display public key to share:**
```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
```

**Verify permissions:**
```powershell
Get-Item $env:USERPROFILE\.ssh\id_ed25519 | Format-List Mode
# Should show -r-------- (read-only)
```

**Friend's action**: Add your public key to their `~/.ssh/authorized_keys` file.

---

## API KEYS FILE (.env.local)

**Location**: `C:\Users\Dell\.env.local`

**Create file:**
```powershell
New-Item -ItemType File -Path "C:\Users\Dell\.env.local"
```

**Add entries** (fill in your actual keys from the official sources):

```
ANTHROPIC_API_KEY=sk-ant-[your-key]
OPENAI_API_KEY=sk-[your-key]
GOOGLE_API_KEY=AIza[your-key]
QWEN_LOCAL_ENDPOINT=http://localhost:11434
QWEN_MODEL=qwen3:8b
MASTER_KEY_PATH=D:\\encryption\\master.key
SYNCTHING_API_KEY=[your-syncthing-token]
```

**Get API keys from official sources:**

Anthropic: https://console.anthropic.com/ → API Keys → Create Key

OpenAI: https://platform.openai.com/ → API Keys → Create new secret key

Google: https://aistudio.google.com/ → Get API Key (in Google Cloud Console)

**Set file permissions:**
```powershell
icacls "C:\Users\Dell\.env.local" /inheritance:r /grant:r "%USERNAME%:F"
```

**Add to .gitignore:**
```powershell
echo ".env.local" >> C:\Users\Dell\.claude\.gitignore
```

**Security rule**: Never commit, never sync to cloud.

---

## CRYPTODRIVE VAULT PASSWORD

**Open Credential Manager:**
```powershell
Control /name Microsoft.CredentialManager
```

**Add credential:**
- Internet address: `CryptoDrive-KD-Brain-Vault`
- Username: `king`
- Password: [strong password, 16+ characters]

**Retrieve in script:**
```powershell
$cred = Get-StoredCredential -Target "CryptoDrive-KD-Brain-Vault"
$password = $cred.GetNetworkCredential().Password
```

---

## SYNCTHING API KEY

**Launch Syncthing**: http://localhost:8384

**Generate key**: Settings → API → Generate

**Store** in .env.local: `SYNCTHING_API_KEY=[token]`

---

## VERIFICATION CHECKLIST

- [ ] Master key in D:\encryption\master.key (read-only)
- [ ] Master key backup in D:\Backups\encryption\master.key.backup (read-only)
- [ ] SSH private key in ~/.ssh/id_ed25519 (read-only)
- [ ] SSH public key shared with friend (only the .pub file)
- [ ] .env.local created with all API keys
- [ ] .env.local is read-only
- [ ] .env.local added to .gitignore
- [ ] Vault password in Credential Manager (not plaintext)
- [ ] Syncthing API key generated and stored

**All credentials local-only. Nothing to cloud.**