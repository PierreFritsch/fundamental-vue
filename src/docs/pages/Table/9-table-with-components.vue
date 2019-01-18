<title>Table</title>
<docs>
You can put other components (for example a simple `FdButton`) in `FdTableCell`.
</docs>

<tip>
If a component you put inside an `FdTableCell` subscribes to `@click`-events, you will most likely wand to use the `.stop`-modifier. Otherwise clicking a button will toggle the selection of the enclosing row.
</tip>

<template>
  <FdTable selectionMode='multiple' :items="tableData">
    <FdTableHeader>
      <FdTableHeaderCell label="First Name" />
      <FdTableHeaderCell label="Last Name" />
      <FdTableHeaderCell label="Building" />
    </FdTableHeader>

    <template slot="row" slot-scope="{item}">
      <FdTableRow @click="onRowClick(item)">
        <FdTableCell>
          <FdButton @click.stop="onButtonClick">{{item.firstName}}</FdButton>
          </FdTableCell>
        <FdTableCell>{{item.lastName}}</FdTableCell>
        <FdTableCell>{{item.building}}</FdTableCell>
      </FdTableRow>
    </template>

  </FdTable>
</template>

<script>
export default {
  methods: {
    onButtonClick() {
      console.log('click on button');
    },
    onRowClick(item) {
      console.log('click on row representing item: %o', item);
    }
  },
  data: () => ({
    tableData: [
      { id: "1", rating: 1, firstName: "Chris", lastName: "Kienle", building: "WFD02" },
      { id: "2", rating: 2, firstName: "Andi", lastName: "Kienle", building: "WFD03" },
      { id: "3", rating: 3, firstName: "Sven", lastName: "Bacia", building: "WFD02" },
      { id: "4", rating: 4, firstName: "Artur", lastName: "Raess", building: "WFD02" },
    ]
  })
};
</script>
