<script setup lang="ts">
import ToggleMode from '../components/ToggleMode.vue'
import { Menubar, MenubarContent, MenubarMenu, MenubarTrigger } from './ui/menubar'
import { Badge } from './ui/badge'
import { SearchIcon, ShoppingCartIcon } from 'lucide-vue-next'
import { Input } from './ui/input'
import { Button } from './ui/button'

let user: any = null
</script>

<template>
  <header class="header-container">
    <Menubar class="menubar-container">
      <div class="menubar-options">
        <h1 class="title">
          <RouterLink to="/">Veggie Vibes</RouterLink>
        </h1>
        <MenubarMenu>
          <MenubarTrigger>Categories</MenubarTrigger>
        </MenubarMenu>
      </div>
      <div class="menubar-options">
        <Input placeholder="Search..." />
        <Button variant="outline">
          <SearchIcon :size="16" />
        </Button>
      </div>
      <div class="menubar-options">
        <MenubarMenu>
          <MenubarTrigger>Account</MenubarTrigger>
          <MenubarContent>
            <MenubarItem v-if="!user">
              <RouterLink to="/account/login">Login</RouterLink>
            </MenubarItem>
            <MenubarItem v-else> <RouterLink to="/account/logout">Logout</RouterLink> </MenubarItem>
          </MenubarContent>
        </MenubarMenu>
        <MenubarMenu>
          <Badge><ShoppingCartIcon /></Badge>
        </MenubarMenu>
        <ToggleMode />
      </div>
    </Menubar>
  </header>
</template>

<style scoped>
.header-container {
  padding: 1rem;
}

.title {
  font: 700 1.25rem 'Poppins';
}

.menubar-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 2rem;
}

.menubar-options {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}
</style>
