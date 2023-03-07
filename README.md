# ishare2-information
ishare2中的google文档镜像

# 修改ishare2脚本

原版
```
function get_initial_information() {
    ID_LIST="$(curl -s $URL_ID_LIST)"

    GOOGLE_SHEETS_ID=$(echo "$ID_LIST" | awk -F= '/^GOOGLE/ { print $2 }')
    BIN_GID=$(echo "$ID_LIST" | awk -F= '/^BIN/ { print $2 }')
    QEMU_GID=$(echo "$ID_LIST" | awk -F= '/^QEMU/ { print $2 }')
    DYNAMIPS_GID=$(echo "$ID_LIST" | awk -F= '/^DYNAMIPS/ { print $2 }')

    URL_PREFIX='https://docs.google.com/spreadsheets/d/e/'$GOOGLE_SHEETS_ID'/pub?gid='
    URL_POSTFIX='&single=true&output=csv'

    BIN_URL=$URL_PREFIX$BIN_GID$URL_POSTFIX
    QEMU_URL=$URL_PREFIX$QEMU_GID$URL_POSTFIX
    DYNAMIPS_URL=$URL_PREFIX$DYNAMIPS_GID$URL_POSTFIX
}
```

修改
```
function get_initial_information() {
    ID_LIST="$(curl -s $URL_ID_LIST)"

    GOOGLE_SHEETS_ID=$(echo "$ID_LIST" | awk -F= '/^GOOGLE/ { print $2 }')
    BIN_GID=$(echo "$ID_LIST" | awk -F= '/^BIN/ { print $2 }')
    QEMU_GID=$(echo "$ID_LIST" | awk -F= '/^QEMU/ { print $2 }')
    DYNAMIPS_GID=$(echo "$ID_LIST" | awk -F= '/^DYNAMIPS/ { print $2 }')

    URL_PREFIX='https://jihulab.com/james-curtis/ishare2-information/-/raw/main/'$GOOGLE_SHEETS_ID'/'
    URL_POSTFIX='.csv'

    BIN_URL=$URL_PREFIX$BIN_GID$URL_POSTFIX
    QEMU_URL=$URL_PREFIX$QEMU_GID$URL_POSTFIX
    DYNAMIPS_URL=$URL_PREFIX$DYNAMIPS_GID$URL_POSTFIX
}
```

# 修改URL常量

修改后
```
function set_url_constants() {
    URL_ID_LIST=https://jihulab.com/james-curtis/ishare2/-/raw/main/id_list
    URL_VERSION=https://jihulab.com/james-curtis/ishare2/-/raw/main/version
    URL_ISHARE2=https://jihulab.com/james-curtis/ishare2/-/raw/main/ishare2
    URL_CHANGELOG_MD=https://jihulab.com/james-curtis/ishare2/-/raw/main/CHANGELOG.md
    URL_CISCO_IOU_KEYGEN_PY=https://jihulab.com/james-curtis/ishare2/-/raw/main/iol/bin/CiscoIOUKeygen.py
    URL_KEEPALIVE_PL=https://jihulab.com/james-curtis/ishare2/-/raw/main/iol/bin/keepalive.pl
    URL_I86BI_LINUX_L2_YML=https://jihulab.com/james-curtis/ishare2/-/raw/main/templates/i86bi_linux_l2/i86bi_linux_l2.yml
    URL_I86BI_LINUX_L3_YML=https://jihulab.com/james-curtis/ishare2/-/raw/main/templates/i86bi_linux_l3/i86bi_linux_l3.yml
    URL_C2600_YML=https://jihulab.com/james-curtis/ishare2/-/raw/main/templates/cisco/c2600.yml
    URL_C1760_YML=https://jihulab.com/james-curtis/ishare2/-/raw/main/templates/cisco/c1760.yml
    URL_UPGRADE_PNETLAB_FROM_4_2_10_TO_5_0_1=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_4.2.10_to_5.0.1/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_4_2_10_TO_5_2_7=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_4.2.10_to_5.2.7/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_5_0_1_TO_5_2_7=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_5.0.1_to_5.2.7/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_2_8=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.2.8/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_2_9=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.2.9/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_0=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.0/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_2=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.2/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_4=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.4/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_5=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.5/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_7=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.7/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_8=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.8/upgrade.sh
    #URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_10=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.10/upgrade.sh
    URL_UPGRADE_PNETLAB_FROM_any_TO_5_3_11=https://jihulab.com/james-curtis/ishare2/-/raw/main/upgrades/from_any_to_5.3.11/upgrade.sh
    URL_UPGRADE_PNETLAB6_INSTALLER='https://unetlab.cloud/api/raw/?path=/UNETLAB%20I/upgrades_pnetlab/Focal/install_pnetlab_v6.sh'
    URL_GUI_APP_ZIP=https://jihulab.com/james-curtis/ishare2/-/raw/main/gui/app.zip
    URL_REQUIREMENTS_GUI_APP=https://jihulab.com/james-curtis/ishare2/-/raw/main/gui/requirements.txt
    URL_ISHARE2_GUI_VERSION=https://jihulab.com/james-curtis/ishare2/-/raw/main/gui/version_gui
}
```