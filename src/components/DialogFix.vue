<template>
    <v-dialog v-model="dialogVisible" max-width="600">
        <v-card>
                <v-card-text>
                    <div v-html="$t('messageVulnerable')"></div><p><strong>{{ itemName }}?</strong></p>
                </v-card-text>
                <v-card-actions>
                    <v-btn color="primary" @click="closeDialog">{{ $t('close') }}</v-btn>
										<v-btn color="error" @click="closeDialog">{{ $t('delete') }}</v-btn>
                </v-card-actions>
        </v-card>
    </v-dialog>
  </template>
  
  <script>
  export default {
    name: "MyDialog",
    props: {
			value: {
				type: Boolean,
				required: true,
			},
      itemName: {
        type: String,
        required: true,
      },
    },
		computed: {
      dialogVisible: {
        get() {
          return this.visible;
        },
        set(value) {
          this.$emit("close", value);
        }
      }
    },
    methods: {
      closeDialog() {
        this.dialogVisible = false;
      },
    },
  };
  </script>

  