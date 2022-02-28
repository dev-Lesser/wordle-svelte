<script>
	import Keyboard from "svelte-keyboard";
	import { Button } from 'sveltestrap';
	import { Card, CardBody, CardText, CardTitle, CardHeader} from 'sveltestrap';
	import { Col, Container, Row } from 'sveltestrap';
	import { fade } from 'svelte/transition';
	
	let visible = true;
	const onKeydown = (event) => {
		console.log(event.detail);
	}
	var template = `
			<div transition:fade class="input-box" style="display:inline-block;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
			</div>
		`
	function checkAnswer(){
		var input = document.querySelectorAll('.input');
		var answer = 'abcde'
		
		for (let i=0; i<5;i++){
		
			if (!input[i].value.length) {
				alert('값을 입력해주세요')
				return;
			}
			if (input[i].value == answer[i]){
				input[i].style.background = 'rgb(21, 168, 21)';
			} else if(answer.includes(input[i].value)) {
				input[i].style.background = 'rgb(229, 255, 0)';
			}
			else{
				input[i].style.background = 'lightgrey';
			}
			input[i].readOnly = true; // readonly 기능 활성화
			input[i].classList.remove('input')
		}
		
		var template = `
			<div transition:fade class="input-box" style="display:inline-block;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
				<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
			</div>
		`
		document.querySelector('.card-text').insertAdjacentHTML('beforeend', template);


	}
</script>

<main>
	<Container>
		<Row cols={2} style="display:flex;justify-content: center;">
			<Col xs="12" sm="12"  md="6">
				<Card body>
					<CardHeader>
						<CardTitle><strong>WORDLE GAME with Svelte</strong></CardTitle>
					</CardHeader>
					<CardBody>
						<CardText style="text-align:center;">
							<div class="input-box" style="display:inline-block;">
								<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
								<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
								<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
								<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
								<input class="input" style="width: 50px;height: 50px;font-size: 30px;text-align: center;margin: 10px; border-radius: 10%;">
							</div>
							<!-- {#if visible}
								<p transition:fade >
									{@html template}
								</p>
							{/if} -->
						</CardText>
						<Button on:click={checkAnswer} block outline color="primary">SUBMIT</Button>
					</CardBody>
				</Card>
			</Col>	
		</Row>
	</Container>
	
	<Keyboard on:keydown="{onKeydown}" />
</main>

<style>
.input {
	width: 50px;
	height: 50px;
	font-size: 30px;
	text-align: center;
	margin: 10px;
	border-radius: 10%;
	transition-property: background-color; /* 전이가 발생되는 시간 명시 */ 
	transition-duration: 1s; /* 1000밀리초와 같다 */ 
	transition-timing-function: linear; /* 등속도 */ 
	transition-delay: .5s; /* 500밀리초 */

}

</style>