<template>
  <CRow>
    <CCol sm="6" lg="4">
      <CWidgetProgressIcon
        header="87.500"
        text="TOTAL CONTACT"
        color="info"
        style="background-color: darkblue; color: aliceblue;"
      >
        <CIcon name="cil-people" height="36" style="color: white;"/>
      </CWidgetProgressIcon>
    </CCol>
    <CCol sm="6" lg="4">
      <CWidgetProgressIcon
        header="117.504"
        text="TOTAL MESSAGES"
        color="danger"
        style="background-color: orange; color: aliceblue;"
      >
        <CIcon name="cil-send" height="36" style="color: white;"/>
      </CWidgetProgressIcon>
    </CCol>
    <CCol sm="6" lg="4">
      <CWidgetProgressIcon
        header="57.335"
        text="PROCESS"
        color="dark"
        style="background-color: green; color: aliceblue;"
      >
        <CIcon name="cil-loop-circular" height="36" style="color: white;"/>
      </CWidgetProgressIcon>
    </CCol>
  </CRow>
</template>

<script>
export default {
  name: 'WidgetsDropdown2'
}
</script>