# Half Life 2 Death Match Docker Image

HL2DM Dedicated Server with Metamod & Sourcemod.

## Prerequisites

You must create the mount directory and give the container full read and write permissions.

## Usage

```
docker run -it --name "HL2DM"                        \
    -v /path/to/local/m:/home/steam/hl2dm            \
    -p 27015:27015                                  \
    -p 27015:27015/udp                              \
    lanopsdev/gameserver-hl2dm
```

You can also use the Entrypoint and CMD to customize configs and plugins like you would normally with SRCDS (Port & Tickrate must be changed via Env Variable)

```
docker run -it --name "HL2DM"                        \
    -v /path/to/local/m:/home/steam/hl2dm            \
    -p 27015:27015                                  \
    -p 27015:27015/udp                              \
    lanopsdev/gameserver-hl2dm                      \
    -maxplayers_override ${SRCDS_MAXPLAYERS}        \
    +sv_pure ${SRCDS_PURE}                          \
    +sv_region ${SRCDS_REGION}                      \
    +sv_lan ${SRCDS_LAN}                            \
    +map ${SRCDS_MAP}                               \
    +game_type ${SRCDS_GAME_TYPE}                   \
    +game_mode ${SRCDS_GAME_MODE}                   \
    +mapgroup ${SRCDS_MAP_GROUP}                    \
    +ip 0.0.0.0

```

## Environment Variables

* SRCDS_PORT - Port Number for the server to run on (Default 27015)
