<template>
  <v-container class="fill-height">
    <v-responsive class="d-flex align-center text-center fill-height">

      <div>
        <v-table>
          <thead>
            <tr>
              <th class="text-left" v-for="heading in headings">
                {{ heading }}
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in csv">
              <td v-for="heading in headings">
                {{ item[heading] }}
              </td>
            </tr>
          </tbody>
        </v-table>
      </div>

      <div class="py-14" />

      <v-row class="d-flex align-center justify-center">
        <v-col cols="auto">
          <v-btn
            href="https://next.vuetifyjs.com/components/all/"
            min-width="164"
            rel="noopener noreferrer"
            target="_blank"
            variant="text"
          >
            <v-icon
              icon="mdi-view-dashboard"
              size="large"
              start
            />

            Components
          </v-btn>
        </v-col>

        <v-col cols="auto">
          <v-btn
            href="https://community.vuetifyjs.com/"
            min-width="164"
            rel="noopener noreferrer"
            target="_blank"
            variant="text"
          >
            <v-icon
              icon="mdi-account-group"
              size="large"
              start
            />

            Community
          </v-btn>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script setup>
  // import mint data
  import csv from '../data/mint_transactions_april_2023.csv'

  // get headings
  // omit headings by adding them to the array below
  const headingsFilter = ['Original Description', 'Account Name', 'Transaction Type']
  const headings = Object.keys(
    csv[0]).filter(heading => !headingsFilter.includes(heading)
  )
  console.log('headings', headings)

  // TODO not in use
  // make a hash id for row keys
  const keyElements = ['Amount', 'Date', 'Description']
  /* csv.map(item => item.key = keyElements.map(element => item[element]).join('')) */
  console.log('csv', csv[0])

</script>
