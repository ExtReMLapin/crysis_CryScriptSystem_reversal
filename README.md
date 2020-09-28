# crysis_CryScriptSystem_reversal
reversing CryScriptSystem.dll to detour lua calls to luajit



|Name                    |section   |Start Address        |
|------------------------|----------|---------------------|
|luaopen_table           |.text     |0x00000000355665F0   |
|luaopen_string          |.text     |0x00000000355646A0   |
|luaopen_package         |.text     |0x000000003555C130   |
|luaopen_os              |.text     |0x000000003555D440   |
|luaopen_math            |.text     |0x000000003555B360   |
|luaopen_io              |.text     |0x0000000035558080   |
|luaopen_debug           |.text     |0x0000000035551BA0   |
|luaopen_base            |.text     |0x000000003554DE00   |
|lua_yield               |.text     |0x0000000035553810   |
|lua_xmove               |.text     |0x0000000035547B10   |
|lua_typename            |.text     |0x0000000035548170   |
|lua_type                |.text     |0x00000000355480A0   |
|lua_touserdata          |.text     |0x0000000035548E50   |
|lua_topointer           |.text     |0x0000000035549000   |
|lua_tonumber            |.text     |0x0000000035548780   |
|lua_tolstring           |.text     |0x0000000035548A50   |
|lua_tointeger           |.text     |0x0000000035548880   |
|lua_tocfunction         |.text     |0x0000000035548D70   |
|lua_toboolean           |.text     |0x0000000035548970   |
|lua_status              |.text     |0x000000003554A460   |
|lua_setupvalue          |.text     |0x000000003554A950   |
|lua_settop              |.text     |0x0000000035547BE0   |
|lua_settable            |.text     |0x0000000035549AD0   |
|lua_setmetatable        |.text     |0x0000000035549F50   |
|lua_setlocal            |.text     |0x0000000035551D90   |
|lua_sethook             |.text     |0x0000000035551BD0   |
|lua_setfield            |.text     |0x0000000035549BC0   |
|lua_setfenv             |.text     |0x000000003554A0D0   |
|lua_resume              |.text     |0x00000000355541F0   |
|lua_replace             |.text     |0x0000000035547E30   |
|lua_remove              |.text     |0x0000000035547C40   |
|lua_rawseti             |.text     |0x0000000035549E20   |
|lua_rawset              |.text     |0x0000000035549CF0   |
|lua_rawgeti             |.text     |0x0000000035549730   |
|lua_rawget              |.text     |0x0000000035549640   |
|lua_rawequal            |.text     |0x0000000035548440   |
|lua_pushvfstring        |.text     |0x0000000035549260   |
|lua_pushvalue           |.text     |0x0000000035547FC0   |
|lua_pushthread          |.text     |0x0000000035549410   |
|lua_pushstring          |.text     |0x00000000355491C0   |
|lua_pushnumber          |.text     |0x0000000035549110   |
|lua_pushnil             |.text     |0x00000000355490F0   |
|lua_pushlstring         |.text     |0x0000000035549150   |
|lua_pushlightuserdata   |.text     |0x00000000355493F0   |
|lua_pushinteger         |.text     |0x0000000035549130   |
|lua_pushfstring         |.text     |0x00000000355492B0   |
|lua_pushcclosure        |.text     |0x0000000035549300   |
|lua_pushboolean         |.text     |0x00000000355493D0   |
|lua_pcall               |.text     |0x000000003554A280   |
|lua_objlen              |.text     |0x0000000035548C50   |
|lua_next                |.text     |0x000000003554A610   |
|lua_newuserdata         |.text     |0x000000003554A7A0   |
|lua_newthread           |.text     |0x0000000035547B90   |
|lua_newstate            |.text     |0x0000000035561C40   |
|lua_load                |.text     |0x000000003554A3C0   |
|lua_isstring            |.text     |0x0000000035548360   |
|lua_isnumber            |.text     |0x0000000035548270   |
|lua_iscfunction         |.text     |0x0000000035548190   |
|lua_insert              |.text     |0x0000000035547D30   |
|lua_getupvalue          |.text     |0x000000003554A810   |
|lua_gettop              |.text     |0x0000000035547BD0   |
|lua_gettable            |.text     |0x0000000035549440   |
|lua_getstack            |.text     |0x0000000035551C30   |
|lua_getmetatable        |.text     |0x00000000355498A0   |
|lua_getlocal            |.text     |0x0000000035551CB0   |
|lua_getinfo             |.text     |0x0000000035552B80   |
|lua_gethookmask         |.text     |0x0000000035551C10   |
|lua_gethookcount        |.text     |0x0000000035551C20   |
|lua_gethook             |.text     |0x0000000035551C00   |
|lua_getfield            |.text     |0x0000000035549520   |
|lua_getfenv             |.text     |0x00000000355499B0   |
|lua_gc                  |.text     |0x000000003554A470   |
|lua_error               |.text     |0x000000003554A600   |
|lua_dump                |.text     |0x000000003554A410   |
|lua_createtable         |.text     |0x0000000035549830   |
|lua_concat              |.text     |0x000000003554A710   |
|lua_close               |.text     |0x0000000035561E90   |
|lua_checkstack          |.text     |0x0000000035547A90   |
|lua_call                |.text     |0x000000003554A220   |
|lua_atpanic             |.text     |0x0000000035547B70   |
|luaL_where              |.text     |0x000000003554AAF0   |
|luaL_unref              |.text     |0x000000003554B3C0   |
|luaL_register           |.text     |0x000000003554C6F0   |
|luaL_ref                |.text     |0x000000003554B2F0   |
|luaL_pushresult         |.text     |0x000000003554B150   |
|luaL_prepbuffer         |.text     |0x000000003554AF40   |
|luaL_optnumber          |.text     |0x000000003554BD60   |
|luaL_optlstring         |.text     |0x000000003554BBC0   |
|luaL_optinteger         |.text     |0x000000003554BEA0   |
|luaL_openlibs           |.text     |0x0000000035556D80   |
|luaL_newmetatable       |.text     |0x000000003554AC10   |
|luaL_loadfile           |.text     |0x000000003554B4D0   |
|luaL_loadbuffer         |.text     |0x000000003554B7A0   |
|luaL_getmetafield       |.text     |0x000000003554ACD0   |
|luaL_findtable          |.text     |0x000000003554AE10   |
|luaL_error              |.text     |0x000000003554AB60   |
|luaL_checkudata         |.text     |0x000000003554B8D0   |
|luaL_checktype          |.text     |0x000000003554B990   |
|luaL_checkstack         |.text     |0x000000003554AC90   |
|luaL_checkoption        |.text     |0x000000003554C530   |
|luaL_checknumber        |.text     |0x000000003554BCA0   |
|luaL_checklstring       |.text     |0x000000003554BB30   |
|luaL_checkinteger       |.text     |0x000000003554BE10   |
|luaL_checkany           |.text     |0x000000003554BA10   |
|luaL_callmeta           |.text     |0x000000003554AD50   |
|luaL_buffinit           |.text     |0x000000003554B2D0   |
|luaL_argerror           |.text     |0x000000003554B7D0   |
|luaL_addvalue           |.text     |0x000000003554B1A0   |
|luaL_addlstring         |.text     |0x000000003554B030   |







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
