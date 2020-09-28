# crysis_CryScriptSystem_reversal
reversing CryScriptSystem.dll to detour lua calls to luajit

missing functions : 


```txt
lua_newstate
lua_close
lua_isuserdata
lua_equal
lua_lessthan
lua_tothread
lua_cpcall
lua_getallocf
lua_setallocf
```


newstate is obviously critical
