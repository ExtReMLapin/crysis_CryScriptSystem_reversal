# crysis_CryScriptSystem_reversal
reversing CryScriptSystem.dll to detour lua calls to luajit

missing functions : 


```txt
lua_isuserdata
lua_equal
lua_lessthan
lua_tothread
lua_cpcall
lua_getallocf
lua_setallocf
luaL_loadstring
luaL_gsub
luaL_addstring
```
`luaL_typerror` got inlined 
![](https://i.imgur.com/SQv2atk.png)

`luaL_newstate` seems to be [unused](https://github.com/CRYTEK/CRYENGINE/blob/6c4f4df4a7a092300d630f8f89d2ebda39183c36/Code/CryEngine/CryScriptSystem/ScriptSystem.cpp#L744)
