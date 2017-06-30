<template>
    <nav :class="classObject">
        <slot></slot>
    </nav>
</template>


<script>
    export default {
        computed: {
            classObject() {
                return [
                    'navbar',
                    this.type ? `navbar-${this.type}` : null,
                    this.variant ? `bg-${this.variant}` : null,
                    this.fixed ? `fixed-${this.fixed}` : null,
                    this.sticky ? 'sticky-top' : null,
                    this.toggleable ? this.toggleableClass : null,
                    this.side ? `side-${this.side}` : null
                ];
            },
            toggleableClass() {
                let className = 'navbar-toggleable';

                if (this.toggleBreakpoint) {
                    className += `-${this.toggleBreakpoint}`;
                }

                return className;
            }
        },
        props: {
            type: {
                type: String,
                default: 'light'
            },
            variant: {
                type: String
            },
            side: {
                type: String
            },
            toggleable: {
                type: Boolean,
                default: false
            },
            toggleBreakpoint: {
                type: String,
                default: null
            },
            fixed: {
                type: String
            },
            sticky: {
                type: Boolean,
                default: false
            }
        }
    };
</script>
<style>
.fixed-right.navbar,
.fixed-left.navbar {
  width: 260px;
  position: fixed;
  border-radius: 0;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 11;
}
.fixed-right.navbar {
  right: 0;
  left: auto;
}
/* unflex */
.fixed-left.navbar,
.fixed-left.navbar .navbar-nav,
.fixed-right.navbar,
.fixed-right.navbar .navbar-nav {
  display: block;
}
@media (min-width: 576px) {
  .fixed-right.navbar.navbar-toggleable .navbar-collapse.
  .fixed-left.navbar.navbar-toggleable .navbar-collapse {
    display: block !important;
  }
}
.fixed-right.navbar .navbar-nav {
  margin: 0 -8px;
}
.fixed-left.navbar .navbar-nav {
  margin: 0 -8px;
}
.fixed-left + .container {
  padding-left: 160px;
}
.fixed-right .navbar-nav > li > .dropdown-menu,
.fixed-left .navbar-nav > li > .dropdown-menu {
  margin-left: 0;
  position: relative;
  float: none;
}
</style>
