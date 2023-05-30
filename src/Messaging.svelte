<script lang="ts">
  import { onMount } from 'svelte';
  import PubNub from 'pubnub';

  // PubNub causing build to fail

  const conf = {
    publishKey: import.meta.env.VITE_PUBLISH_KEY,
    subscribeKey: import.meta.env.VITE_SUBSCRIBE_KEY,
    secretKey: import.meta.env.VITE_SECRET_KEY,
    userId: 'myUniqueUserId'
  }

  const pubnub = new PubNub({...conf});

  let count = 0;

  onMount(async () => {
    console.log('/dashboard/+layout.svelte: mount');

    const listener = {
      status: (statusEvent) => {
        console.log('status', statusEvent);
        if (statusEvent.category === 'PNConnectedCategory') {
          console.log('<Messaging /> pubnub connected');
        }
      },
      message: (messageEvent) => {
        count++;
        const { type, data } = messageEvent.message;
        console.log('<Messaging /> onMessage')
        console.log(messageEvent);
      },
      presence: (presenceEvent) => {
        // handle presence
        console.log('presence:', presenceEvent);
      }
    };

    pubnub.subscribe({
      channels: ['my-channel.*']
    });

    pubnub.addListener(listener);
  });
</script>

<div>Messages: {count}</div>

<pre>
  {JSON.stringify(conf, null, 2)}
</pre>