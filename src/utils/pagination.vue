<template>

<ul class="am-pagination" v-class="am-pagination-centered: centered, am-pagination-right: right">
  <li v-class="am-disabled: page === 1"><a v-link="link(page-1)">&laquo;</a></li>
  <li v-repeat="p in pages" v-class="am-active: p === page">
    <a v-link="link(p)" v-if="p !== -1">{{ p }}</a>
    <a href="javascript:;" v-if="p === -1">...</a>
  </li>
  <li v-class="am-disabled: page === total"><a v-link="link(page+1)">&raquo;</a></li>
</ul>

</template>

<script>

/**
 * Create Pagination
 * @param {Number} total 总页数
 * @param {Number} current 当前页页码
 */
function repaint(total, current) {

  var pages = [];

  if (total < 1) {
    pages.push(1);
    return pages;
  }

  if (total < 9) {
    for (var i = 0; i < total; ++i) {
      pages.push(i + 1);
    }
  } else {
    if (current < 5) {
      if (current === 4) {
        for (var i = 0; i < 5; ++i) {
          pages.push(i + 1);
        }
      } else {
        for (var i = 0; i < 4; ++i) {
          pages.push(i + 1);
        }
      }
      pages.push(-1);
      pages.push(total - 1);
      pages.push(total);
    } else if (current > total - 4) {
      pages.push(1);
      pages.push(2);
      pages.push(-1);
      if (current === total - 3) {
        for (var i = -1; i < 4; ++i) {
          pages.push(total - 3 + i);
        }
      } else {
        for (var i = 0; i < 4; ++i) {
          pages.push(total - 3 + i);
        }
      }
    } else {
      pages.push(1);
      pages.push(-1);
      for (var i = -2; i < 3; ++i) {
        pages.push(current + i);
      }
      pages.push(-1);
      pages.push(total);
    }
  }

  return pages;
};

module.exports = {
  props: {
    centered: {
      type: Boolean,
      default: false
    },
    right: {
      type: Boolean,
      default: false
    },
    page: {
      type: Number,
      default: 1
    },
    total: {
      type: Number,
      default: 0
    },
    link: {
      type: Function,
      default: function(p) {
        return '?page=' + p;
      }
    }
  },

  computed: {
    pages: function() {
      return repaint(this.total, this.page);
    }
  }
};

</script>
