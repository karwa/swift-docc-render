<!--
  This source file is part of the Swift.org open source project

  Copyright (c) 2021-2022 Apple Inc. and the Swift project authors
  Licensed under Apache License v2.0 with Runtime Library Exception

  See https://swift.org/LICENSE.txt for license information
  See https://swift.org/CONTRIBUTORS.txt for Swift project authors
-->

<template>
  <div class="contenttable-section">
    <div class="section-title">
      <slot name="title">
        <h3 class="title">{{ title }}</h3>
      </slot>
    </div>
    <div class="section-content">
      <slot name="abstract" />
      <slot name="discussion" />
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContentTableSection',
  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
@import 'docc-render/styles/_core.scss';

.title + .contenttable-section {
  margin-top: 0;
}

.contenttable-section {
  align-items: baseline;
  padding-top: $contenttable-spacing-single-side;

  &:last-child {
    margin-bottom: 0;
  }

  .section-title {
    padding-bottom: 8px;
    border-bottom: 1px solid var(--color-grid);
  }
}

/deep/ .title {
  @include font-styles(label);
}

@include breakpoint(small) {
  .contenttable-section {
    align-items: unset;
    border-top: none;
    display: inherit;
    margin: 0;
  }

  .section {
    &-title,
    &-content {
      padding: 0;
    }
  }
}
</style>
