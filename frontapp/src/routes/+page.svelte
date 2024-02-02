<script>
    import { onMount } from 'svelte';

    let welcomeMessage = '';

    const checkLoginStatus = async () => {
        try {
            const response = await fetch('/api/v1/members/login', {
                method: 'GET',
                credentials: 'include',  // 쿠키를 요청에 포함시키기 위해 필요
            });

            if (response.ok) {
                welcomeMessage = '환영합니다!';
            } else {
                welcomeMessage = '로그인을 해주세요.';
            }
        } catch (error) {
            console.error('로그인 상태 확인 중 오류 발생:', error);
        }
    }

    onMount(checkLoginStatus);  // 컴포넌트가 마운트될 때 로그인 상태를 확인
</script>

<h1>{welcomeMessage}</h1>