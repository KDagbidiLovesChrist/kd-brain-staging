# END-TO-END TOOL STACK REFERENCE
**Version 1.0 · Complete multi-agent orchestration system**
**Built from 5 scout consensus reports · Production-proven patterns**

---

## QUICK REFERENCE TABLE

| Layer | Tool | Version | Purpose | Cost | Status |
|-------|------|---------|---------|------|--------|
| **Orchestration** | LangGraph | 0.1.50+ | Graph based workflows, fault recovery | Free | ✅ |
| **Orchestration** | Mastra | 1.0.0+ | Multi model router (Claude/Gemini/GPT/Qwen) | Free | ✅ |
| **Orchestration** | Google A2A Protocol | 1.0 | Agent encryption boundaries, OAuth 2.0 | Free | ✅ |
| **Encryption** | libsodium.js | 0.7.0+ | Local encrypt before sync (NaCl boxes) | Free | ✅ |
| **Encryption** | CryptoDrive | Latest | Encrypt filesystem before cloud upload | Free | ✅ |
| **Cloud Sync** | rclone | 1.67.0+ | 150+ cloud backends, exact folder mirror | Free | ✅ |
| **Cloud Sync** | Windows Task Scheduler | Native | Nightly sync automation | Free (OS) | ✅ |
| **Redundancy** | rsync | 3.2.7+ (Windows port) | One way backups | Free | ✅ |
| **Redundancy** | Syncthing | 1.27.0+ | Bidirectional P2P sync | Free | ✅ |
| **Dashboard** | Mission Control | 2.0.1+ | Kanban board + activity stream | Free | ✅ |
| **Visualization** | ECharts | 5.5.0+ | 3D real time data (100k+ points) | Free | ✅ |
| **Visualization** | Tremor | 3.17.0+ | React UI components | Free | ✅ |
| **Agent Router** | Qwen3 (Local) | Latest | Local LLM, zero per call cost | Free | ✅ |
| **APIs** | OpenAI (GPT 4o) | Latest | Reasoning via router | Paid (usage based) | ✅ |
| **APIs** | Google (Gemini) | 2.0 Pro | Vision & research via router | Free/Paid | ✅ |
| **APIs** | Anthropic (Claude) | Sonnet 4+ | Coordination via router | Paid | ✅ |
| **Backup** | GitHub (Private) | N/A | Code + audit log repository | Free | ✅ |
| **Tunnel** | Tailscale | Latest | Encrypted P2P tunnel | Free | ✅ |
| **Monitoring** | OpenTelemetry | Latest | Agent tracing + audit | Free | ✅ |

---

## LAYER 1: ORCHESTRATION (Agent Coordination)

### 1.1 LangGraph
**Purpose:** Graph-based workflow engine. Define states, conditional branching, checkpoints for fault recovery.

**Official source:** https://github.com/langchain-ai/langgraph

**Version:** 0.1.50+

**Package manager:** pip (Python) / npm (Node.js)

**Key files location:**
- Workflow definition: `.claude/commands/workflow_orchestration.py`
- Checkpoint store: `~/.langgraph/checkpoints.db` (SQLite)

**Cost:** Free (open-source, Apache 2.0)

---

### 1.2 Mastra
**Purpose:** Multi-model router. One API interface, routes to Claude/Gemini/GPT/Qwen based on task type and cost.

**Official source:** https://mastra.ai/

**Version:** 1.0.0+

**Package manager:** npm (Node.js) / pip (Python)

**Configuration:** Stored in `.env.local` (local only, never synced to cloud)

**Cost:** Free (open-source). Pays only per actual API call to each model.

---

### 1.3 Google A2A Protocol
**Purpose:** Open standard for agent-to-agent communication with OAuth 2.0 + RSA signing and encryption.

**Official source:** https://github.com/google-ai-agent-2-agent/a2a-protocol

**Governance:** Linux Foundation (50+ enterprise partners)

**Setup:** Download SDK from official repo, create agent card with public key, sign messages.

**Cost:** Free (open standard)

---

## LAYER 2: ENCRYPTION (Data Protection)

### 2.1 libsodium.js
**Purpose:** Lightweight encryption library. NaCl boxes for symmetric encryption, sealed boxes for public-key.

**Official sources:**
- JavaScript: https://github.com/jedisct1/libsodium.js
- Python: https://github.com/pyca/pynacl

**Version:** 0.7.0+ (JavaScript), 1.5.0+ (Python)

**Package manager:** npm / pip

**Master key storage:** `D:\encryption\master.key` (BitLocker encrypted, local D: drive only)

**Backup location:** `D:\Backups\encryption\master.key.backup` (same physical drive, same encryption)

**Never stored in:** OneDrive, Google Drive, GitHub, email, or any cloud service

**Cost:** Free (open-source, MIT license)

---

### 2.2 CryptoDrive
**Purpose:** Filesystem-level encryption. Encrypt folder structure before rclone syncs to cloud.

**Official source:** https://github.com/Apollo3zehn/CryptoDrive

**Download method:** Visit releases page, download binary for Windows

**Installation location:** `C:\Program Files\CryptoDrive`

**Setup process:** Create vault → add folder → mount → sync → unmount

**Cost:** Free (open-source, MIT license)

---

## LAYER 3: CLOUD SYNC (Multi-Cloud Mirror)

### 3.1 rclone
**Purpose:** Sync to 150+ cloud backends while preserving exact folder structure.

**Official source:** https://rclone.org/

**Version:** 1.67.0+

**Configuration file location:** `~/.config/rclone/rclone.conf`

**Setup process:** Run `rclone config` (interactive, browser-based OAuth for Google Drive/OneDrive)

**Features:**
- Preserves empty folders
- Preserves metadata and timestamps
- Supports incremental syncs
- Dry-run mode for testing

**Cost:** Free (open-source, MIT license)

---

### 3.2 Windows Task Scheduler
**Purpose:** Schedule rclone syncs to run nightly without manual intervention.

**Access:** `taskschd.msc` (native Windows)

**Scheduled tasks to create:**
- nightly-sync-google-drive (2:00 AM)
- nightly-sync-onedrive (2:15 AM)
- nightly-rsync-backup (3:00 AM)

**Cost:** Free (native Windows OS feature)

---

## LAYER 4: DISTRIBUTED REDUNDANCY (Laptop ↔ Friend's PC)

### 4.1 rsync (One-Way Backups)
**Purpose:** Nightly one-way backups to friend's PC. Zero split-brain risk by design.

**Official sources:**
- Documentation: https://linux.die.net/man/1/rsync
- Windows port: https://github.com/WinMerge/rsync-for-windows

**Version:** 3.2.7+

**Package manager:** Chocolatey (Windows) / Homebrew (macOS) / apt/yum (Linux)

**Authentication method:** SSH key (passwordless, no plaintext credentials in scripts)

**Backup destination:** Friend's PC `/home/friend/backups/kd-brain-YYYYMMDD/`

**Failover method:** If this laptop fails, friend's PC backup is read-only and copyable back via SSH.

**Cost:** Free (open-source, GPL v3)

---

### 4.2 Syncthing (Bidirectional Real-Time Sync)
**Purpose:** Keep working files in sync between laptop and friend's PC in real-time.

**Official sources:**
- Project: https://syncthing.net/
- Documentation: https://docs.syncthing.net/
- Windows GUI wrapper: Cascable SyncTrazor (https://github.com/canton7/SyncTrayzor)

**Version:** 1.27.0+

**Setup method:** GUI-based device pairing via Tailscale encrypted tunnel

**Configuration location:** `~/.config/syncthing/config.xml`

**Conflict handling:** Auto-keeps both versions as `.sync-conflict-` files for manual review

**Cost:** Free (open-source, MPL-2.0 license)

---

## LAYER 5: DASHBOARD & VISUALIZATION

### 5.1 Mission Control
**Purpose:** Kanban board (task status), live activity stream, memory browser for audit log.

**Official source:** https://github.com/builderz-labs/mission-control

**Version:** 2.0.1+

**Setup method:** Clone from GitHub, `npm install`, `npm run dev`

**Access:** http://localhost:3200

**Database:** `./data/missions.db` (SQLite, stored locally)

**Cost:** Free (open-source)

---

### 5.2 ECharts (3D Real-Time Visualization)
**Purpose:** Agent state graph (3D), data flow animation, handle 100k+ data points real-time.

**Official sources:**
- Project: https://echarts.apache.org/
- Documentation: https://echarts.apache.org/handbook/
- 3D support: echarts-gl module

**Version:** 5.5.0+

**Package manager:** npm

**Integration:** React component + WebSocket for real-time updates from agents

**Cost:** Free (open-source, Apache 2.0)

---

### 5.3 Tremor (React UI Components)
**Purpose:** Pre-built dashboard cards, metrics, progress bars, chart components.

**Official sources:**
- Project: https://www.tremor.so/
- GitHub: https://github.com/tremorlabs/tremor

**Version:** 3.17.0+

**Package manager:** npm

**Integration:** React components in dashboard, pairs with Recharts

**Cost:** Free (open-source)

---

## LAYER 6: API SERVICES (Model Providers)

### 6.1 Anthropic Claude API
**Purpose:** Coordination, final judgment, complex multi-step reasoning via Mastra router.

**Official source:** https://console.anthropic.com/

**Version:** Latest (Sonnet 4, Opus 5, etc.)

**Cost:**
- Consumer API: $20/month per seat (Claude Sonnet 4)
- Pro API: Usage based (~$0.003-$0.015 per 1K output tokens for Opus 5)

**API key location:** `.env.local` (stored locally, never synced)

**Documentation:** https://docs.anthropic.com/

---

### 6.2 OpenAI GPT-4o API
**Purpose:** Specialized reasoning, complex analysis via Mastra router.

**Official source:** https://platform.openai.com/

**Version:** Latest (GPT-4o, GPT-4o mini)

**Cost:**
- GPT-4o: $0.015 per 1K input, $0.060 per 1K output tokens
- GPT-4o mini: $0.00015 per 1K input, $0.0006 per 1K output tokens

**API key location:** `.env.local` (stored locally, never synced)

**Documentation:** https://platform.openai.com/docs/

---

### 6.3 Google Gemini API
**Purpose:** Vision (image analysis), research tasks via Mastra router.

**Official source:** https://aistudio.google.com/

**Version:** Latest (Gemini 2.0 Flash, Gemini Pro Vision)

**Cost:**
- Free tier: 50 requests/minute, 15 requests/day
- Paid (Gemini 2.0 Pro): $0.00075 per 1K input, $0.003 per 1K output tokens

**API key location:** `.env.local` (stored locally, never synced)

**Documentation:** https://ai.google.dev/

---

### 6.4 Qwen3 (Local, via Ollama)
**Purpose:** Local LLM reasoning. No internet connection, zero API cost per call.

**Official sources:**
- Ollama: https://ollama.ai/
- Qwen models: https://ollama.ai/library/qwen

**Version:** Latest (Qwen3:8b recommended for balance of speed/quality)

**Model variants:**
- Qwen3:3b (faster, lower quality)
- Qwen3:8b (recommended, 0.5s latency)
- Qwen3:14b (slower, higher quality, if GPU available)

**Server:** Ollama runs as background service, exposes API at `http://localhost:11434`

**Cost:** €0 (fully local, zero per-call cost)

---

## LAYER 7: BACKUP & VERSION CONTROL

### 7.1 GitHub (Private Repository)
**Purpose:** Engine code backup, audit log immutable record, version history.

**Official source:** https://github.com/

**Repositories to create/use:**
- `klarnow-logos-engine` (already created, for engine code only)
- `audit-log` (new, for mission audit records)

**Features:**
- Private repos free
- Audit trails
- Immutable record of all changes

**Cost:** Free (private repos included)

---

### 7.2 Tailscale (Encrypted Tunnel)
**Purpose:** Secure peer-to-peer tunnel between laptop and friend's PC. No port forwarding, encrypted.

**Official sources:**
- Project: https://tailscale.com/
- Documentation: https://tailscale.com/kb/

**Version:** Latest

**Setup process:**
1. Download from official site
2. Run `tailscale up`
3. Authenticate in browser
4. Note Tailscale IP (100.x.y.z)
5. Repeat on friend's PC

**Security:** All traffic encrypted, private between authorized devices only

**Cost:** Free (personal use, unlimited devices)

---

## ENVIRONMENT CONFIGURATION

**File location:** `C:\Users\Dell\.env.local`

**File permissions:** Read-only to system account, no cloud sync

**Contents structure:** API keys, encryption key paths, service endpoints

**Security rules:**
- Never commit to Git (add to .gitignore immediately)
- Never sync to OneDrive, Google Drive, or any cloud service
- Never share via email, messaging, or network
- Backup: `D:\encryption\` only (BitLocker encrypted)

**Example entries (DO NOT PASTE ACTUAL VALUES):**
```
ANTHROPIC_API_KEY=[your-key-here]
OPENAI_API_KEY=[your-key-here]
GOOGLE_API_KEY=[your-key-here]
QWEN_LOCAL_ENDPOINT=http://localhost:11434
MASTER_KEY_PATH=D:\\encryption\\master.key
RCLONE_CONFIG_PATH=~/.config/rclone/rclone.conf
TAILSCALE_IP=100.x.y.z
```

---

## COMPLETE DATA FLOW (Architecture Overview)

**Master Copy:**
```
C:\Users\Dell\.claude/ (8.02GB)
├─ projects/klarnow-logos-sandbox/engine/ → GitHub (engine code)
├─ the-truth/ (LOCAL ONLY, never sync)
├─ finances/ (LOCAL ONLY, never sync)
└─ [rest of brain]

D:\ (Backup Drive, BitLocker)
├─ Backups/claude-brain/ (mirror of C:\Users\Dell\.claude)
└─ encryption/master.key (encryption key, local only)
```

**Cloud Mirror (Nightly rclone syncs):**
```
Google Drive /King/.claude/
└─ [public/non-sensitive content]

OneDrive /King/.claude/
└─ [public/non-sensitive content]
```

**Distributed Backup (Nightly rsync):**
```
Friend's PC /home/friend/backups/
├─ kd-brain-20260827/
└─ latest → symlink to today's backup
```

**Real-Time Sync (Syncthing bidirectional):**
```
C:\Users\Dell\.claude\projects/ ↔ Friend's PC /home/friend/projects/
```

**Agent Orchestration:**
```
LangGraph (workflow state machine)
  ↓
Mastra (model router)
  ├→ Qwen3:8b (local, fast)
  ├→ Claude (via Anthropic API)
  ├→ GPT-4o (via OpenAI API)
  └→ Gemini (via Google API)
```

**Visualization:**
```
Mission Control (http://localhost:3200)
├─ Kanban board (task status)
├─ Activity stream (real-time)
└─ Memory browser

ECharts 3D (agent state graph, WebSocket real-time)

Tremor (dashboard metrics, React components)
```

---

## STARTUP SEQUENCE (Every Night)

**0:30 AM**: System wakes, D: drive auto mounts (BitLocker unlocks)

**0:45 AM**: Startup script runs:
- Mount CryptoDrive vault
- Start Syncthing service
- Start Mission Control dashboard
- Start Ollama (Qwen3)

**1:00 AM**: Syncthing connects to friend's PC

**2:00 AM**: Windows Task Scheduler: rclone sync to Google Drive

**2:15 AM**: Windows Task Scheduler: rclone sync to OneDrive

**3:00 AM**: Windows Task Scheduler: rsync backup to friend's PC

**6:00 AM**: CryptoDrive vault auto decrypts (4 hour idle timeout)

---

## COST BREAKDOWN (Monthly)

| Service | Free Option | Paid Option | Notes |
|---------|-------------|------------|-------|
| **All open source tools** | ✅ | (free) | LangGraph, Mastra, libsodium, rclone, rsync, Syncthing, Mission Control, ECharts, Tremor |
| **Claude API** | (none) | $20+ | Consumer minimum $20/mo; Pro varies |
| **OpenAI API** | (none) | ~$10-50 | Usage based, variable |
| **Gemini API** | ✅ (50 req/min) | €0-30 | Free tier sufficient for most; paid tier optional |
| **Qwen3 Local** | ✅ | (free) | Zero per call cost |
| **GitHub** | ✅ | (free) | Private repos free |
| **Tailscale** | ✅ | (free) | Free for personal |
| **Google Drive** | 15GB | €1.99/mo | 100GB plan |
| **OneDrive** | 5GB | €0.99/mo | 100GB plan |
| **TOTAL** | **€0-5/mo** | **€25-80+/mo** | Depends on API intensity |

---

## TESTING & DEPLOYMENT CHECKLIST

**Before deploying any component:**

✅ Orchestration
- [ ] LangGraph checkpoint store created
- [ ] Mastra can reach all 4 models (Qwen, Claude, Gemini, GPT)
- [ ] A2A Protocol agent card created

✅ Encryption
- [ ] libsodium library installed and imported
- [ ] CryptoDrive vault created and mounts
- [ ] master.key stored in D:\encryption\ (not cloud)

✅ Cloud Sync
- [ ] rclone authenticated to Google Drive
- [ ] rclone authenticated to OneDrive
- [ ] Test dry-run: `rclone sync --dry-run`
- [ ] Windows Task Scheduler tasks created

✅ Redundancy
- [ ] Syncthing paired with friend's PC
- [ ] rsync SSH key auth works (no password prompt)
- [ ] Tailscale tunnel connects

✅ Dashboard
- [ ] Mission Control runs on http://localhost:3200
- [ ] ECharts renders without console errors
- [ ] Tremor components display

✅ APIs
- [ ] Mastra reaches Qwen3:8b locally
- [ ] Mastra reaches Claude API
- [ ] Mastra reaches Gemini API
- [ ] Mastra reaches GPT-4o API

✅ Backup & Version Control
- [ ] GitHub audit-log repo created
- [ ] .env.local excluded from .gitignore
- [ ] klarnow-logos-engine branch pushed to GitHub

---

## DOCUMENTATION LINKS

**Core Tools:**
- LangGraph: https://langchain-ai.github.io/langgraph/
- Mastra: https://mastra.ai/
- Google A2A: https://github.com/google-ai-agent-2-agent/a2a-protocol

**Encryption:**
- libsodium.js: https://github.com/jedisct1/libsodium.js
- CryptoDrive: https://github.com/Apollo3zehn/CryptoDrive

**Cloud & Backup:**
- rclone: https://rclone.org/
- rsync: https://linux.die.net/man/1/rsync
- Syncthing: https://docs.syncthing.net/

**Dashboard:**
- Mission Control: https://github.com/builderz-labs/mission-control
- ECharts: https://echarts.apache.org/
- Tremor: https://www.tremor.so/

**APIs:**
- Claude: https://docs.anthropic.com/
- OpenAI: https://platform.openai.com/docs/
- Gemini: https://ai.google.dev/
- Ollama: https://ollama.ai/

**Infrastructure:**
- Tailscale: https://tailscale.com/kb/
- GitHub: https://docs.github.com/

---

**Status:** Reference document complete. All 20 tools with official sources, versions, configuration locations, and cost data.

**Next step:** King approves stack → Separate implementation guide created (setup scripts, step-by-step walkthrough).