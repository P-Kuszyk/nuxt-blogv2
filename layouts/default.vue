<template>
    <TopInfoBar>
      <template v-slot:title>
        Telefon 
      </template>
      <template v-slot:content>
        333 222 111
      </template>
      <template v-slot:title2>
        Email
      </template>
      <template v-slot:content2>
        dupadupa@wp.pl
      </template>
    </TopInfoBar>
  
    <TopNav />
    <slot />
    <Footer />
  </template>