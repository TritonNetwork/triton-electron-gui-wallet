<template>
<q-layout view="hHh Lpr lFf">
    <q-layout-header class="shift-title">
        <main-menu />
        <q-toolbar-title>
            <div class="flex items-center justify-center" style="margin-top:0px">
                <div style="padding-left: auto; padding-right: auto; padding-top: auto; padding-bottom: auto;">
                    <img src="statics/xeq_logo_with_padding.png" height="60">
                </div>
            </div>
        </q-toolbar-title>
    </q-layout-header>

    <q-page-container>
        <!-- <AddressHeader :address="info.address" :title="info.name" /> -->
        <WalletDetails />

        <div class="app-content">
            <div class="navigation row items-end">
                <router-link to="/wallet">
                    <q-btn
                        class="large-btn primary"
                        label="Transactions"
                        size="md"
                        icon-right="swap_horiz"
                        align="left"
                    />
                </router-link>
                <router-link to="/wallet/send">
                    <q-btn
                        class="large-btn primary"
                        label="Send"
                        size="md"
                        icon-right="arrow_right_alt"
                        align="left"
                    />
                </router-link>
                <router-link to="/wallet/receive">
                    <q-btn
                        class="large-btn"
                        label="Receive"
                        size="md"
                        icon-right="save_alt"
                        align="left"
                    />
                </router-link>
                <router-link to="/wallet/staking-pools">
                    <q-btn
                        class="large-btn primary"
                        label="Staking Pools"
                        size="md"
                        icon-right="arrow_right_alt"
                        align="left"
                    />
                </router-link>
                <router-link to="/wallet/addressbook" class="address">
                    <q-btn
                        class="single-icon"
                        size="md"
                        icon="person"
                    />
                </router-link>

            </div>
            <div class="hr-separator" />
            <keep-alive>
                <router-view />
            </keep-alive>
        </div>
    </q-page-container>

    <status-footer />

</q-layout>
</template>

<script>
const { clipboard } = require("electron")
import { openURL } from "quasar"
import { mapState } from "vuex"
import WalletDetails from "components/wallet_details"
import Formattriton from "components/format_triton"
import StatusFooter from "components/footer"
import MainMenu from "components/mainmenu"
export default {
    name: "LayoutDefault",
    computed: mapState({
        theme: state => state.gateway.app.config.appearance.theme,
        info: state => state.gateway.wallet.info,
    }),
    data() {
        return {
            selectedTab: "tab-1",
        }
    },
    methods: {
        openURL,
    },
    components: {
        StatusFooter,
        MainMenu,
        WalletDetails
    }
}
</script>

<style lang="scss">
.navigation {
    padding: 8px 12px;

    > * {
        margin: 2px 0;
        margin-right: 12px;
    }

    > *:last-child {
        margin-right: 0px;
    }

    .address {
        margin-left: auto;
    }

    .single-icon {
        width: 38px;
        padding: 0;
    }

    .large-btn {
        width: 180px;
        .q-btn-inner > *:last-child {
            margin-left: auto;
        }

    }
}

</style>
