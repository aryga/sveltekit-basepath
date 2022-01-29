<script context="module">
    export const prerender = true;

    import {base} from '$app/paths';

    export async function load({fetch}) {
        const res = await fetch(`${base}/mypage/mypage.json`);
        if (res.ok) {
            const t = await res.json();
            return {
                props: {
                    mytext: t.mytext
                }
            };
        }

        return {
            status: res.status,
            error: new Error(`Could not load text from endpoint`)
        };
    }
</script>


<script>
    export let mytext = '';
</script>

<h1>Welcome to test page</h1>
<p>Text: {mytext}</p>
