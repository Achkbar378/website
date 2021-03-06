<template>
	<span
		v-if="nav.link"
		class="app-navigation"
		:class="nav.class"
		title="App navigation"
	>
		<a class="app-link" :href="nav.link + entry">
			<MaterialIcon
				v-if="nav.icon"
				class="app-icon"
				:icon-name="nav.icon"
			/>
			<span class="app-label">{{ nav.text }}</span>
			<slot />
		</a>
	</span>
	<span
		v-else
		class="app-navigation"
		:class="nav.class"
		title="App navigation"
	>
		<MaterialIcon v-if="nav.icon" class="app-icon" :icon-name="nav.icon" />
		<span class="app-label">{{ nav.text }}</span>
		<slot />
	</span>
</template>

<script>
/**
 * Code example: <Navigation item="library"/>
 */
export default {
	props: {
		item: {
			type: String,
			required: true,
		},
		entry: {
			type: String,
			default: "",
		},
	},
	computed: {
		nav() {
			// prettier-ignore
			return {
				/* Menus */
				library: { text: "Library", icon: "collections_bookmark" },
				updates: { text: "Updates", icon: "new_releases" },
				history: { text: "History", icon: "history" },
				browse: { text: "Browse", icon: "explore" },
				more: { text: "More", icon: "more_horiz" },
				/* Actions */
				update_library: { text: "Update library", icon: "refresh" },
				search: { text: "Search", icon: "search" },
				filter: { text: "Filter", icon: "filter_list" },
				edit: { text: "EDIT", icon:"edit" },
				delete: { text: "DELETE", icon:"delete" },
				/* More */
				downloaded_only: { text: "Downloaded only", icon: "cloud_off" },
				download_queue: { text: "Download queue", icon: "get_app" },
				source_migration: { text: "Source migration", icon: "compare_arrows" },
				settings: { text: "Settings", icon: "settings", link: "/help/guides/settings/" },
				about: { text: "About", icon: "info" },
				/* Settings */
				settings_general: { text: "General", icon: "tune", link: "/help/guides/settings/general" },
				settings_library: { text: "Library", icon: "collections_bookmark" },
				settings_reader: { text: "Reader", icon: "chrome_reader_mode", link: "/help/guides/settings/reader" },
				settings_downloads: { text: "Downloads", icon: "get_app", link: "/help/guides/settings/downloads" },
				settings_tracking: { text: "Tracking", icon: "autorenew", link: "/help/guides/settings/tracking" },
				settings_backup: { text: "Backup", icon: "backup", link: "/help/guides/settings/backup" },
				settings_security: { text: "Security", icon: "security" },
				settings_advanced: { text: "Advanced", icon: "code", link: "/help/guides/settings/advanced" },
				/* Library info */
				bookmark: { text: "Add to library", icon: "favorite_border" },
				bookmarked: { text: "In library", icon: "favorite" },
				set_categories: { text: "Set categories", icon: "label" },
				share: { text: "Share", icon: "share" },
				webview: { text: "WebView", icon: "public" },
				/* Browse */
				button_latest: { text: "LATEST" },
				button_browse: { text: "BROWSE" },
				tab_sources: { text: "SOURCES" },
				tab_extensions: { text: "EXTENSIONS" },
				/* Sites */
				tachiyomi: { text: "Tachiyomi" },
				mangadex: { text: "MangaDex" },
				/* Misc */
				install: { text: "INSTALL", class:"ext-installation" },
				reorder: { text: "Reorder", icon:"reorder" },
				/* Legacy */
				old_library: { text: "My library", icon: "class" },
				old_catalogues: { text: "Catalogues", icon: "explore" },
				old_overflow: { text: "Overflow menu", icon: "more_vert" },
				old_backup: { text: "Backup", icon: "cloud_upload", link: "/help/guides/settings/backup" },
				old_extensions: { text: "Extensions", icon: "extension" },
			}[this.item];
		},
	},
};
</script>

<style lang="stylus">
.app-navigation
	white-space nowrap
	.app-icon,
	.app-label
		color $accentColorSecondary
		font-weight 500
		font-size 1em
	.app-icon
		vertical-align top
	.app-link
		&:hover
			cursor pointer
			text-decoration none !important
			.app-icon,
			.app-label
				color $accentColor
	.app-image
		max-height 1.5em
		vertical-align sub
	&.ext-installation
		border 1px solid $accentColorSecondary
		padding 0px 0px 2px 4px
		margin-right 5px
		border-radius 4px
	&:hover
		cursor default
</style>
