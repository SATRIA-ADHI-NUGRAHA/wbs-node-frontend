<template>
  <div>
    <WidgetsDropdown/>
    <CRow>
      <CCol md="12">
        <CCard>
          <CCardHeader>
            Sender List
          </CCardHeader>
          <CCardBody>
            <CDataTable
              class="mb-0 table-inline"
              hover
              :items="tableItems"
              :fields="tableFields"
              head-color="white"
              sorted
              pagination
              items-per-page-select
              :items-per-page="5"
              table-filter
            >
              <td slot="avatar" class="text-center" slot-scope="{item}">
                <div class="c-avatar">
                  <img :src="item.avatar.url" class="c-avatar-img" alt="">
                  <span
                    class="c-avatar-status"
                    :class="`bg-${item.avatar.status || 'secondary'}`"
                  ></span>
                </div>
              </td>
              <td slot="user" slot-scope="{item}">
                <div>{{item.user.name}}</div>
                <div class="small text-muted">
                  <span>
                    <template v-if="item.user.new">New</template>
                    <template v-else>Recurring</template>
                  </span> | Registered: {{item.user.registered}}
                </div>
              </td>
              <td
                slot="country"
                slot-scope="{item}"
                class="text-center"
              >
                <CIcon
                  :name="item.country.flag"
                  height="25"
                />
              </td>
              <td slot="usage" slot-scope="{item}">
                <div class="clearfix">
                  <div class="float-left">
                    <strong>{{item.usage.value}}%</strong>
                  </div>
                  <div class="float-right">
                    <small class="text-muted">{{item.usage.period}}</small>
                  </div>
                </div>
                <CProgress
                  class="progress-xs"
                  v-model="item.usage.value"
                  :color="color(item.usage.value)"
                />
              </td>
              <td
                slot="payment"
                slot-scope="{item}"
                class="text-center"
              >
                <CIcon
                  :name="item.payment.icon"
                  height="25"
                />
              </td>
              <td slot="activity" slot-scope="{item}">
                <div class="small text-muted">Last login</div>
                <strong>{{item.activity}}</strong>
              </td>
              <td slot="action">
                <div class="medium text-muted">
                  <CButton color="success">
                    <CIcon name="cilSend"/>
                  </CButton>
                  |
                  <CButton color="warning">
                    <CIcon name="cilPencil"/>
                  </CButton>
                  |
                  <CButton color="danger">
                    <CIcon name="cilDelete"/>
                  </CButton>
                </div>
              </td>
            </CDataTable>
          </CCardBody>
        </CCard>
      </CCol>
    </CRow>
  </div>
</template>

<script>
import WidgetsDropdown from './widgets/WidgetsDropdown'

export default {
  name: 'Sender',
  components: {
    WidgetsDropdown,
  },
  data () {
    return {
      selected: 'Month',
      tableItems: [
        {
          avatar: { url: 'img/avatars/1.jpg', status: 'success' },
          user: { name: 'Yiorgos Avraamu', new: true, registered: 'Jan 1, 2015' },
          phone: '085775044336',
          email: 'aho123@gmail.com',
          activity: 'Last year',
          action: 'send | edit | delete'
        },
        {
          avatar: { url: 'img/avatars/2.jpg', status: 'danger' },
          user: { name: 'Avram Tarasios', new: false, registered: 'Jan 1, 2015' },
          phone: '085775044337',
          email: 'aho123@gmail.com',
          activity: '1 sec ago',
          action: 'send | edit | delete'
        },
        {
          avatar: { url: 'img/avatars/3.jpg', status: 'danger' },
          user: { name: 'Quintin Ed', new: true, registered: 'Jan 1, 2015' },
          phone: '085775044338',
          email: 'aho123@gmail.com',
          activity: '5 minutes ago',
          action: 'send | edit | delete'
        },
        {
          avatar: { url: 'img/avatars/4.jpg', status: 'success' },
          user: { name: 'Enéas Kwadwo', new: true, registered: 'Jan 1, 2015' },
          phone: '085775044339',
          email: 'aho123@gmail.com',
          activity: 'Last week',
          action: 'send | edit | delete'
        },
        {
          avatar: { url: 'img/avatars/5.jpg', status: 'success' },
          user: { name: 'Agapetus Tadeáš', new: true, registered: 'Jan 1, 2015' },
          phone: '085775044335',
          email: 'aho123@gmail.com',
          activity: '1 day ago',
          action: 'send | edit | delete'
          
        },
        {
          avatar: { url: 'img/avatars/6.jpg', status: 'danger' },
          user: { name: 'Friderik Dávid', new: true, registered: 'Jan 1, 2015' },
          phone: '085775044334',
          email: 'aho123@gmail.com',
          activity: 'Last week',
          action: 'send | edit | delete'
        }
      ],
      tableFields: [
        { key: 'avatar', label: '', _classes: 'text-center' },
        { key: 'user', label: 'Name' },
        { key: 'phone', label: 'Phone number' },
        { key: 'email' },
        { key: 'activity' },
        { key: 'action'}
      ]
    }
  },
  methods: {
    color (value) {
      let $color
      if (value <= 25) {
        $color = 'info'
      } else if (value > 25 && value <= 50) {
        $color = 'success'
      } else if (value > 50 && value <= 75) {
        $color = 'warning'
      } else if (value > 75 && value <= 100) {
        $color = 'danger'
      }
      return $color
    }
  }
}
</script>
