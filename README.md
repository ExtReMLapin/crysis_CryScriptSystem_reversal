# crysis_CryScriptSystem_reversal
reversing CryScriptSystem.dll to detour lua calls to luajit

missing functions : 


```txt
lua_close
lua_isuserdata
lua_equal
lua_lessthan
lua_tothread
lua_cpcall
lua_getallocf
lua_setallocf
luaL_getn
luaL_setn
luaL_typerror
luaL_checkudata
luaL_loadstring
luaL_gsub
luaL_addstring
luaL_addvalue
```
