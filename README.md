# AJAX

function getAjax(url,callback,data){
	var str = ""
	for(var i in data){
		str = str + i + "=" + data[i] + "&";
	}
	var d = new Date();
	url = url + "?" + str + "_t=" + d.getTime();
	var ajax = new XMLHttpRequest();
	ajax.open("GET",url)
	ajax.onreadystatechange = function(){
		if(ajax.readyState == 4 && ajax.status == 200){
			callback(ajax.responseText)
		}
	}
	ajax.send(null);
}

function postAjax(url,callback,data){
	var str = ""
	for(var i in data){
		str = str + i+"="+data[i] + "&";
	}
	str = str.slice(0,str.length-1);
	var d = new Date();
	url = url + "?_t="+d.getTime();
	var ajax = new XMLHttpRequest();
	ajax.open("POST",url,true);
	ajax.onreadystatechange = function(){
		if(ajax.readyState == 4 && ajax.status == 200){
			callback(ajax.responseText)
		}
	}
	ajax.setRequestHeader("Content-Type","application/x-www-form-urlencoded");
	ajax.send(str);
}
