<template>
  <div
    v-observe-visibility="initialVisibleState || visible ? false : {
      callback: onVisibilityChanged,
      once: true,
    }"
    :class="{ placeholder: !visible }"
  >
    <template
      v-if="visible"
    >
      <p
        class="videoIndex"
      >
        <font-awesome-icon
          v-if="isCurrentVideo"
          class="videoIndexIcon"
          :icon="['fas', 'play']"
        />
        <span
          v-else
          class="index"
        >
          {{ videoIndex + 1 }}
        </span>
        <font-awesome-icon
          v-if="isPlaylistFiltered"
          tabindex="0"
          role="img"
          class="videoIndexIcon"
          :title="$t('Video.Playlist Search result')"
          :icon="['fas', 'magnifying-glass']"
        />
      </p>
      <ft-list-video
        :data="data"
        :playlist-id="playlistId"
        :playlist-type="playlistType"
        :playlist-index="playlistIndex"
        :playlist-reverse="playlistReverse"
        :playlist-shuffle="playlistShuffle"
        :playlist-loop="playlistLoop"
        :playlist-item-id="playlistItemId"
        force-list-type="list"
        :appearance="appearance"
        :always-show-add-to-playlist-button="alwaysShowAddToPlaylistButton"
        :quick-bookmark-button-enabled="quickBookmarkButtonEnabled"
        :can-move-video-up="canMoveVideoUp"
        :can-move-video-down="canMoveVideoDown"
        :can-remove-from-playlist="canRemoveFromPlaylist"
        @pause-player="pausePlayer"
        @move-video-up="moveVideoUp"
        @move-video-down="moveVideoDown"
        @remove-from-playlist="removeFromPlaylist"
      />
    </template>
  </div>
</template>

<script src="./ft-list-video-numbered.js" />
<style scoped src="./ft-list-video-numbered.css" />
