# Mummummi
멈뭄멈뭄

## Code

	@EventHandler
	public void onChat(PlayerChatEvent event) {
		
		StringBuffer mes = new StringBuffer();
		for (int i = 0; i < event.getMessage().length(); i++) {
			char str = event.getMessage().charAt(i);
			if ((int)str >= 0XAC00) {
				char uniVal = (char) (str - 0xAC00);
				/*
				 * first - 초성
				 * middle - 중성
				 * last - 종성
				 * */
				char first = (char) (((uniVal - (uniVal % 28))/28)/21);
				char middle = (char) (((uniVal - (uniVal % 28))/28)%21);
				char last = (char) (uniVal %28);
				if((int)first == 11){
					first =6;
				}
				if(last == 21){
					last = 16;
				}
				 str = (char)(0xAC00 + 28 * 21 *(first) + 28 * (middle) + (last));
			}
			mes.append(str);
		}
		event.setMessage(mes.toString());
		
	}

}

