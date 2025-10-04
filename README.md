# FlowdexMCP

MCP server providing enhanced FTP/SFTP operations with smart sync, search, and direct file access.

## Features

- 🔄 **Smart Sync** - Only transfer changed files
- 🔍 **Search & Tree** - Find files by pattern, view entire directory structures
- 📝 **Direct Access** - Read/write file contents without downloading
- 📦 **Batch Operations** - Upload/download multiple files at once
- 🔐 **Multi-Profile** - Support for multiple FTP servers via `.ftpconfig`
- ⚡ **FTP & SFTP** - Automatic protocol detection

## Quick Start

### 1. Install

```bash
npm install -g flowdex-mcp
```

### 2. Configure Credentials

**Option A: Environment Variables**

```bash
# Windows
setx FTPMCP_HOST "ftp.example.com"
setx FTPMCP_USER "username"
setx FTPMCP_PASSWORD "password"

# Linux/Mac
export FTPMCP_HOST="ftp.example.com"
export FTPMCP_USER="username"
export FTPMCP_PASSWORD="password"
```

**Option B: Project Config File (Recommended)**

Create `.ftpconfig` in your project directory:

```json
{
  "production": {
    "host": "ftp.example.com",
    "user": "prod-user",
    "password": "your-password",
    "port": 21
  },
  "staging": {
    "host": "sftp://staging.example.com",
    "user": "staging-user",
    "password": "your-password",
    "port": 22
  }
}
```

### 3. Add to Amp Code

Open **Settings → MCP Servers**, click **Add Server**:

- **Server Name:** `FTP` (or any name you prefer)
- **Command or URL:** `ftp-mcp-server`
- **Arguments:** (leave empty)
- **Environment Variables:** (leave empty if using system env vars)

Click **Update Server** and restart Amp.

## Available Tools

### Connection
- `ftp_connect` - Switch between named profiles

### File Operations
- `ftp_get_contents` - Read file without downloading
- `ftp_put_contents` - Write content directly
- `ftp_upload` / `ftp_download` - Single file transfer
- `ftp_batch_upload` / `ftp_batch_download` - Multiple files
- `ftp_delete` - Remove files
- `ftp_copy` - Duplicate files (SFTP only)
- `ftp_rename` - Move/rename files

### Directory Operations
- `ftp_list` - List directory contents
- `ftp_tree` - Recursive directory tree
- `ftp_search` - Find files by pattern
- `ftp_mkdir` / `ftp_rmdir` - Create/remove directories

### Metadata
- `ftp_stat` - File metadata (size, modified date)
- `ftp_exists` - Check if file exists
- `ftp_disk_space` - Server space info (SFTP only)
- `ftp_chmod` - Change permissions (SFTP only)

### Advanced
- `ftp_sync` - Smart sync local ↔ remote

## Usage Examples

```
"Connect to my production FTP"
"Show me the file tree of /public_html"
"Search for all .js files"
"Read the contents of config.php"
"Sync my local dist folder to /www"
"Check if backup.sql exists"
```

## Development

Clone and install locally:

```bash
git clone https://github.com/Kynlos/FlowdexMCP.git
cd FlowdexMCP
npm install
npm install -g .
```

## License

MIT

---

**Author:** Kynlo
