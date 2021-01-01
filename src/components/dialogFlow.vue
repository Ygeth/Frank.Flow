<template>
  <div class="dialogFlow">
    <df-messenger
      intent=""
      chat-title="Holiwi :D"
      :agent-id="agentId"
      language-code="es"
      @df-response-received="eventResponse"
    />
  </div>
</template>

<script>
export default {
  name: 'dialogFlow',
  data:()=>({
    agentId: process.env.VUE_APP_GOOGLE_AGENTID
  }),
  created() {
    let externalScript = document.createElement('script');
    externalScript.setAttribute('src', 'https://www.gstatic.com/dialogflow-console/fast/messenger/bootstrap.js?v=1');
    document.head.appendChild(externalScript);
  },
  methods: {
    eventResponse(event){
      console.log(event)
      let payload = {};
      payload.action = event.detail.response.queryResult.action;
      payload.parameters = event.detail.response.queryResult.parameters;
      console.log(payload)
      console.log(payload.parameters)
      this.$emit('newAction', payload);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
df-messenger {
  --df-messenger-bot-message: #878fac;
  --df-messenger-button-titlebar-color: #df9b56;
  --df-messenger-chat-background-color: #fafafa;
  --df-messenger-font-color: white;
  --df-messenger-send-icon: #878fac;
  --df-messenger-user-message: #479b3d;
  }
</style>
