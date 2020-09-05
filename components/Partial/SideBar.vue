<template>
  <v-list dense>
    <v-list-item @click link>
      <v-list-item-action>
        <v-icon>fas fa-home</v-icon>
      </v-list-item-action>
      <v-list-item-content>
        <v-list-item-title class="subtitle-1">Dashboard</v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-list-group prepend-icon="fas fa-users" group>
      <template v-slot:activator>
        <v-list-item-title class="subtitle-1">User Group</v-list-item-title>
      </template>

      <v-list-item @click link>
        <v-list-item-action>
          <v-icon class="ml-3">fas fa-user</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title>User</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list-group>
  </v-list>
</template>

<script>
export default {
  //$router.push('/admin/users')
};
</script>