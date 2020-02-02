<template lang="pug">
  div
    div
      #wrapper
        my-sidebar
        #content-wrapper.d-flex.flex-column
          #content
            my-header
            .container-fluid
              .d-sm-flex.align-items-center.justify-content-between.mb-4
                h1.h3.mb-0.text-gray-800 Dashboard
                a.d-none.d-sm-inline-block.btn.btn-sm.btn-primary.shadow-sm(href='#')
                  i.fas.fa-download.fa-sm.text-white-50
                  |  Generate
                  |                   Report
              .row
                .col-xl-3.col-md-6.mb-4
                  .card.border-left-primary.shadow.h-100.py-2
                    .card-body
                      .row.no-gutters.align-items-center
                        .col.mr-2
                          .text-xs.font-weight-bold.text-primary.text-uppercase.mb-1
                            | Earnings (Monthly)
                          .h5.mb-0.font-weight-bold.text-gray-800
                            | $40,000
                        .col-auto
                          i.fas.fa-calendar.fa-2x.text-gray-300
                .col-xl-3.col-md-6.mb-4
                  .card.border-left-success.shadow.h-100.py-2
                    .card-body
                      .row.no-gutters.align-items-center
                        .col.mr-2
                          .text-xs.font-weight-bold.text-success.text-uppercase.mb-1
                            | Earnings (Annual)
                          .h5.mb-0.font-weight-bold.text-gray-800
                            | $215,000
                        .col-auto
                          i.fas.fa-dollar-sign.fa-2x.text-gray-300
                .col-xl-3.col-md-6.mb-4
                  .card.border-left-info.shadow.h-100.py-2
                    .card-body
                      .row.no-gutters.align-items-center
                        .col.mr-2
                          .text-xs.font-weight-bold.text-info.text-uppercase.mb-1
                            | Tasks
                          .row.no-gutters.align-items-center
                            .col-auto
                              .h5.mb-0.mr-3.font-weight-bold.text-gray-800
                                | 50%
                            .col
                              .progress.progress-sm.mr-2
                                .progress-bar.bg-info(role='progressbar' style='width: 50%' aria-valuenow='50' aria-valuemin='0' aria-valuemax='100')
                        .col-auto
                          i.fas.fa-clipboard-list.fa-2x.text-gray-300
                .col-xl-3.col-md-6.mb-4
                  .card.border-left-warning.shadow.h-100.py-2
                    .card-body
                      .row.no-gutters.align-items-center
                        .col.mr-2
                          .text-xs.font-weight-bold.text-warning.text-uppercase.mb-1
                            | Pending Requests
                          .h5.mb-0.font-weight-bold.text-gray-800
                            | 18
                        .col-auto
                          i.fas.fa-comments.fa-2x.text-gray-300
              .row
                .col-xl-8.col-lg-7
                  .card.shadow.mb-4
                    .card-header.py-3.d-flex.flex-row.align-items-center.justify-content-between
                      h6.m-0.font-weight-bold.text-primary
                        | Earnings Overview
                      .dropdown.no-arrow
                        a#dropdownMenuLink.dropdown-toggle(href='#' role='button' data-toggle='dropdown' aria-haspopup='true' aria-expanded='false')
                          i.fas.fa-ellipsis-v.fa-sm.fa-fw.text-gray-400
                        .dropdown-menu.dropdown-menu-right.shadow.animated--fade-in(aria-labelledby='dropdownMenuLink')
                          .dropdown-header Dropdown Header:
                          a.dropdown-item(href='#') Action
                          a.dropdown-item(href='#') Another action
                          .dropdown-divider
                          a.dropdown-item(href='#') Something else here
                    .card-body
                      .chart-area
                        canvas#myAreaChart
                .col-xl-4.col-lg-5
                  .card.shadow.mb-4
                    .card-header.py-3.d-flex.flex-row.align-items-center.justify-content-between
                      h6.m-0.font-weight-bold.text-primary
                        | Revenue Sources
                      .dropdown.no-arrow
                        a#dropdownMenuLink.dropdown-toggle(href='#' role='button' data-toggle='dropdown' aria-haspopup='true' aria-expanded='false')
                          i.fas.fa-ellipsis-v.fa-sm.fa-fw.text-gray-400
                        .dropdown-menu.dropdown-menu-right.shadow.animated--fade-in(aria-labelledby='dropdownMenuLink')
                          .dropdown-header Dropdown Header:
                          a.dropdown-item(href='#') Action
                          a.dropdown-item(href='#') Another action
                          .dropdown-divider
                          a.dropdown-item(href='#') Something else here
                    .card-body
                      .chart-pie.pt-4.pb-2
                        canvas#myPieChart
                      .mt-4.text-center.small
                        span.mr-2
                          i.fas.fa-circle.text-primary
                          |  Direct
                        span.mr-2
                          i.fas.fa-circle.text-success
                          |  Social
                        span.mr-2
                          i.fas.fa-circle.text-info
                          |  Referral
          my-footer
      a.scroll-to-top.rounded(href='#page-top')
        i.fas.fa-angle-up
      #logoutModal.modal.fade(tabindex='-1' role='dialog' aria-labelledby='exampleModalLabel' aria-hidden='true')
        .modal-dialog(role='document')
          .modal-content
            .modal-header
              h5#exampleModalLabel.modal-title
                | Ready to Leave?
              button.close(type='button' data-dismiss='modal' aria-label='Close')
                span(aria-hidden='true') &times;
            .modal-body
              | Select &quot;Logout&quot; below if you are ready to end your current
              | session.
            .modal-footer
              button.btn.btn-secondary(type='button' data-dismiss='modal')
                | Cancel
              a.btn.btn-primary(href='login.html') Logout
    nuxt
</template>

<script>
/*eslint-disable */
import MySidebar from "@@/components/ui/Sidebar"
import MyHeader from "@@/components/ui/Header"
import MyFooter from "@@/components/ui/Footer"

export default {
  components: { MySidebar, MyHeader, MyFooter },
  mounted() {
    !(function(t) {
      'use strict'
      t('#sidebarToggle, #sidebarToggleTop').on('click', function(o) {
        t('body').toggleClass('sidebar-toggled'),
          t('.sidebar').toggleClass('toggled'),
          t('.sidebar').hasClass('toggled') &&
            t('.sidebar .collapse').collapse('hide')
      }),
        t(window).resize(function() {
          t(window).width() < 768 && t('.sidebar .collapse').collapse('hide')
        }),
        t('body.fixed-nav .sidebar').on(
          'mousewheel DOMMouseScroll wheel',
          function(o) {
            if (768 < t(window).width()) {
              var e = o.originalEvent,
                l = e.wheelDelta || -e.detail
              ;(this.scrollTop += 30 * (l < 0 ? 1 : -1)), o.preventDefault()
            }
          }
        ),
        t(document).on('scroll', function() {
          100 < t(this).scrollTop()
            ? t('.scroll-to-top').fadeIn()
            : t('.scroll-to-top').fadeOut()
        }),
        t(document).on('click', 'a.scroll-to-top', function(o) {
          var e = t(this)
          t('html, body')
            .stop()
            .animate(
              { scrollTop: t(e.attr('href')).offset().top },
              1e3,
              'easeInOutExpo'
            ),
            o.preventDefault()
        })
    })(jQuery)
  }
}
</script>
