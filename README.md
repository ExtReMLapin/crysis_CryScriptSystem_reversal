# crysis x64 ryScriptSystem_reversal
reversing CryScriptSystem.dll to detour lua calls to luajit


|Name                 |section|IDA reported Address|Static address|
|---------------------|-------|--------------------|--------------|
|luaopen_table        |.text  |0x00000000355665F0  |0x655f0       |
|luaopen_string       |.text  |0x00000000355646A0  |0x636a0       |
|luaopen_package      |.text  |0x000000003555C130  |0x5b130       |
|luaopen_os           |.text  |0x000000003555D440  |0x5c440       |
|luaopen_math         |.text  |0x000000003555B360  |0x5a360       |
|luaopen_io           |.text  |0x0000000035558080  |0x57080       |
|luaopen_debug        |.text  |0x0000000035551BA0  |0x50ba0       |
|luaopen_base         |.text  |0x000000003554DE00  |0x4ce00       |
|lua_yield            |.text  |0x0000000035553810  |0x52810       |
|lua_xmove            |.text  |0x0000000035547B10  |0x46b10       |
|lua_typename         |.text  |0x0000000035548170  |0x47170       |
|lua_type             |.text  |0x00000000355480A0  |0x470a0       |
|lua_touserdata       |.text  |0x0000000035548E50  |0x47e50       |
|lua_topointer        |.text  |0x0000000035549000  |0x48000       |
|lua_tonumber         |.text  |0x0000000035548780  |0x47780       |
|lua_tolstring        |.text  |0x0000000035548A50  |0x47a50       |
|lua_tointeger        |.text  |0x0000000035548880  |0x47880       |
|lua_tocfunction      |.text  |0x0000000035548D70  |0x47d70       |
|lua_toboolean        |.text  |0x0000000035548970  |0x47970       |
|lua_status           |.text  |0x000000003554A460  |0x49460       |
|lua_setupvalue       |.text  |0x000000003554A950  |0x49950       |
|lua_settop           |.text  |0x0000000035547BE0  |0x46be0       |
|lua_settable         |.text  |0x0000000035549AD0  |0x48ad0       |
|lua_setmetatable     |.text  |0x0000000035549F50  |0x48f50       |
|lua_setlocal         |.text  |0x0000000035551D90  |0x50d90       |
|lua_sethook          |.text  |0x0000000035551BD0  |0x50bd0       |
|lua_setfield         |.text  |0x0000000035549BC0  |0x48bc0       |
|lua_setfenv          |.text  |0x000000003554A0D0  |0x490d0       |
|lua_resume           |.text  |0x00000000355541F0  |0x531f0       |
|lua_replace          |.text  |0x0000000035547E30  |0x46e30       |
|lua_remove           |.text  |0x0000000035547C40  |0x46c40       |
|lua_rawseti          |.text  |0x0000000035549E20  |0x48e20       |
|lua_rawset           |.text  |0x0000000035549CF0  |0x48cf0       |
|lua_rawgeti          |.text  |0x0000000035549730  |0x48730       |
|lua_rawget           |.text  |0x0000000035549640  |0x48640       |
|lua_rawequal         |.text  |0x0000000035548440  |0x47440       |
|lua_pushvfstring     |.text  |0x0000000035549260  |0x48260       |
|lua_pushvalue        |.text  |0x0000000035547FC0  |0x46fc0       |
|lua_pushthread       |.text  |0x0000000035549410  |0x48410       |
|lua_pushstring       |.text  |0x00000000355491C0  |0x481c0       |
|lua_pushnumber       |.text  |0x0000000035549110  |0x48110       |
|lua_pushnil          |.text  |0x00000000355490F0  |0x480f0       |
|lua_pushlstring      |.text  |0x0000000035549150  |0x48150       |
|lua_pushlightuserdata|.text  |0x00000000355493F0  |0x483f0       |
|lua_pushinteger      |.text  |0x0000000035549130  |0x48130       |
|lua_pushfstring      |.text  |0x00000000355492B0  |0x482b0       |
|lua_pushcclosure     |.text  |0x0000000035549300  |0x48300       |
|lua_pushboolean      |.text  |0x00000000355493D0  |0x483d0       |
|lua_pcall            |.text  |0x000000003554A280  |0x49280       |
|lua_objlen           |.text  |0x0000000035548C50  |0x47c50       |
|lua_next             |.text  |0x000000003554A610  |0x49610       |
|lua_newuserdata      |.text  |0x000000003554A7A0  |0x497a0       |
|lua_newthread        |.text  |0x0000000035547B90  |0x46b90       |
|lua_newstate         |.text  |0x0000000035561C40  |0x60c40       |
|lua_load             |.text  |0x000000003554A3C0  |0x493c0       |
|lua_isstring         |.text  |0x0000000035548360  |0x47360       |
|lua_isnumber         |.text  |0x0000000035548270  |0x47270       |
|lua_iscfunction      |.text  |0x0000000035548190  |0x47190       |
|lua_insert           |.text  |0x0000000035547D30  |0x46d30       |
|lua_getupvalue       |.text  |0x000000003554A810  |0x49810       |
|lua_gettop           |.text  |0x0000000035547BD0  |0x46bd0       |
|lua_gettable         |.text  |0x0000000035549440  |0x48440       |
|lua_getstack         |.text  |0x0000000035551C30  |0x50c30       |
|lua_getmetatable     |.text  |0x00000000355498A0  |0x488a0       |
|lua_getlocal         |.text  |0x0000000035551CB0  |0x50cb0       |
|lua_getinfo          |.text  |0x0000000035552B80  |0x51b80       |
|lua_gethookmask      |.text  |0x0000000035551C10  |0x50c10       |
|lua_gethookcount     |.text  |0x0000000035551C20  |0x50c20       |
|lua_gethook          |.text  |0x0000000035551C00  |0x50c00       |
|lua_getfield         |.text  |0x0000000035549520  |0x48520       |
|lua_getfenv          |.text  |0x00000000355499B0  |0x489b0       |
|lua_gc               |.text  |0x000000003554A470  |0x49470       |
|lua_error            |.text  |0x000000003554A600  |0x49600       |
|lua_dump             |.text  |0x000000003554A410  |0x49410       |
|lua_createtable      |.text  |0x0000000035549830  |0x48830       |
|lua_concat           |.text  |0x000000003554A710  |0x49710       |
|lua_close            |.text  |0x0000000035561E90  |0x60e90       |
|lua_checkstack       |.text  |0x0000000035547A90  |0x46a90       |
|lua_call             |.text  |0x000000003554A220  |0x49220       |
|lua_atpanic          |.text  |0x0000000035547B70  |0x46b70       |
|luaL_where           |.text  |0x000000003554AAF0  |0x49af0       |
|luaL_unref           |.text  |0x000000003554B3C0  |0x4a3c0       |
|luaL_register        |.text  |0x000000003554C6F0  |0x4b6f0       |
|luaL_ref             |.text  |0x000000003554B2F0  |0x4a2f0       |
|luaL_pushresult      |.text  |0x000000003554B150  |0x4a150       |
|luaL_prepbuffer      |.text  |0x000000003554AF40  |0x49f40       |
|luaL_optnumber       |.text  |0x000000003554BD60  |0x4ad60       |
|luaL_optlstring      |.text  |0x000000003554BBC0  |0x4abc0       |
|luaL_optinteger      |.text  |0x000000003554BEA0  |0x4aea0       |
|luaL_openlibs        |.text  |0x0000000035556D80  |0x55d80       |
|luaL_newmetatable    |.text  |0x000000003554AC10  |0x49c10       |
|luaL_loadfile        |.text  |0x000000003554B4D0  |0x4a4d0       |
|luaL_loadbuffer      |.text  |0x000000003554B7A0  |0x4a7a0       |
|luaL_getmetafield    |.text  |0x000000003554ACD0  |0x49cd0       |
|luaL_findtable       |.text  |0x000000003554AE10  |0x49e10       |
|luaL_error           |.text  |0x000000003554AB60  |0x49b60       |
|luaL_checkudata      |.text  |0x000000003554B8D0  |0x4a8d0       |
|luaL_checktype       |.text  |0x000000003554B990  |0x4a990       |
|luaL_checkstack      |.text  |0x000000003554AC90  |0x49c90       |
|luaL_checkoption     |.text  |0x000000003554C530  |0x4b530       |
|luaL_checknumber     |.text  |0x000000003554BCA0  |0x4aca0       |
|luaL_checklstring    |.text  |0x000000003554BB30  |0x4ab30       |
|luaL_checkinteger    |.text  |0x000000003554BE10  |0x4ae10       |
|luaL_checkany        |.text  |0x000000003554BA10  |0x4aa10       |
|luaL_callmeta        |.text  |0x000000003554AD50  |0x49d50       |
|luaL_buffinit        |.text  |0x000000003554B2D0  |0x4a2d0       |
|luaL_argerror        |.text  |0x000000003554B7D0  |0x4a7d0       |
|luaL_addvalue        |.text  |0x000000003554B1A0  |0x4a1a0       |
|luaL_addlstring      |.text  |0x000000003554B030  |0x4a030       |







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
