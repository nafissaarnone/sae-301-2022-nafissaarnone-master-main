<script setup lang="ts">
import { supabase, user } from '../supabase'

async function signInWithFacebook() {
    try {
        // @ts-ignore
    const { data, error } = await supabase.auth.signIn({
        provider: 'facebook',
    });
    if (error) throw error;
    } catch (error) {
        // @ts-ignore
        alert(error.error_description || error.message)
    }
}


async function signout() {
    const { error } = await supabase.auth.signOut()
}
</script>

<template>
    <div class="connexion">
        <button id="facebook" @click="signInWithFacebook()">
            Se connecter avec Facebook
        </button>
        <button id="facebook" @pointerdown="supabase.auth.signIn({ provider: 'facebook' })">
            <p class="fb1"> SE CONNECTER AVEC FACEBOOK </p><img class="fb" src="../../public/images/facebook.png"
                alt="" />
        </button>
        <button class="invisible" id="facebook" v-if="user" @pointerdown="supabase.auth.signOut()">
            Se déconnecter ({{ user.email }})
        </button>
        <button id="google" @pointerdown="supabase.auth.signIn({ provider: 'google' })">
            <p class="fb1"> SE CONNECTER AVEC GOOGLE </p><img class="fb" src="../../public/images/google.png" alt="" />
        </button>

    </div>
</template>