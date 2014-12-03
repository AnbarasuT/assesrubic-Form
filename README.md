assesrubic-Form
===============

form
var savedState,savedState1,savedState2;
var pageContainer, menuContainer, page0, formContainer;
var pageno=1;
var setrow_1=setrow_2=setrow_3=setrow_4=setrow_5=setrow_6=false;
var rowSel1=rowSel2=rowSel3=rowSel4=rowSel5=rowSel6=null;
var inv = new Array();
var tar = new Array();
var removeEndElemet,addcount=0;
var getPos,setPos;
var refresh=false;
var resetState=false;
var prePage=nextPage=1;
var dataArray = new Array();
var saveStageArray = new Array();
var prevBlock=nextBlock=false;
var nextMoveblock=false;
var nosave=true;
var txtPos;
var saveEnable=false;
var saving=prevMoveblock=true;
$(document).ready(
    function(){
	var table=["<div id=\"blocker\" onclick=\"instruct()\" ><div class=\"question\" onclick=\"instruct()\"><div style=\"position:absolute; left:2%; top:4%; opacity:0.6;\" ><div><img src=\"images/btInfoOn.png\" width=\"25px\" height=\"27px\" /></div></div><span style=\"text-align:left; font-family:myFontfamily; left:40px; line-height:1.4em; width:370px; position:absolute; top:45px;\">Write your ideas in the Column &#x0201C;Specific to This Project&#x0201D; and in the blank criterion row.</span><i style=\"font-size: 21px;  float:right; opacity: .6; position:absolute;right:10px;top:5px;\" class=\"closeBtn icon icon-emove\" ><strong>&times;</strong></i></div></div>"];
        pageContainer = $("<div id=\"interactive-container\" />");
        menuContainer = $("<div id=\"page-container\" />");
        page0 = $("<div id=\"page-0\" class=\"page\" />");
	header = $("<div class=\"head\">Rubric Project Write-Up and Presentation</div>");
	nameTxt=$("<div class=\"nameTxt\"><input class=\"inTxt\" type=\"text\" placeholder=\"Student&#39;s Name\" /></div>")
	
	formContainer = $("<div id=\"group1\"><div class=\"title\"><div id=\"addPage\"><div class=\"button_Box\"><span class=\"addicon\"></span><span style=\"position:absolute;top:13px;left:75px;line-height:20px;color:#FFF380;font-weight:normal;\">Add<br/> Page</span></div></div><div id=\"label1\">Description</div><div id=\"label2\">Score</div><div id=\"label3\">Scoring Criterion</div><div id=\"label4\">General Description of a 4 Score</div><div id=\"label5\">Specific to this Project</div><div class=\"label6 \">4</div><div class=\"label7\">3</div><div class=\"label8\">2</div><div class=\"label9\">1</div><div class=\"label10\">0</div></div><div id=\"droppableArea1\" class=\"area\"><div id=\"row1\"><div id=\"rowTxt1\"><span class=\"rowinTxt alignTxt\" style=\"top:45.5px;position:absolute; text-align:center;\">Clarity</span></div><div id=\"rowTxt2\"><span class=\"rowinTxt2\">Written: Neat, legible, good use of conventions.<br/> Spoken: Appropriate volume and pacing, visuals easy to <br/>see and understand.</span></div><div id=\"rowTxt3\"><span class=\"rowText\" style=\"top:5px;\"><textarea class=\"inputTxt\" onkeypress=\"wrapTxt()\" onchange=\"changestates()\" onblur=\"onFocusOutHandler(event);\"></textarea></span></div><div class=\"label6 rowTxt4 row1box \" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label7 rowTxt4 row1box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label8 rowTxt4 row1box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label9 rowTxt4 row1box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label10 rowTxt4 row1box\" onclick=\"validate(this)\"><span class=\"checkicon\" style=\" background-position:center; \"></span></div></div><div id=\"row2\"><div id=\"rowTxt5\"><span class=\"rowinTxt alignTxt\" style=\"top:32px;position:absolute;\">Mathematical Representations</span></div><div id=\"rowTxt6\"><span class=\"rowinTxt2\">Appropriate and accurate vocabulary, mathematical notation, graphs, tables, figures, and patterns.</span></div><div id=\"rowTxt7\"><span class=\"rowText\"><textarea  class=\"inputTxt\"  onchange=\"changestates()\"></textarea></span></div><div class=\"label6 rowTxt4 noBorder row2box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label7 rowTxt4 noBorder row2box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label8 rowTxt4 noBorder row2box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label9 rowTxt4 noBorder row2box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label10 rowTxt4 noBorder row2box\" onclick=\"validate(this)\"><span class=\"checkicon\" style=\" background-position:center; \"></span></div></div><div id=\"row3\"><div id=\"rowTxt8\"><span class=\"rowinTxt alignTxt\" style=\"top:41px;position:absolute;\">Sequence</span></div><div id=\"rowTxt9\"><span class=\"rowinTxt2\" style=\"top:32px;position:absolute;\">Organized, easy to follow,<br/> chain of thought is coherent.</span></div><div id=\"rowTxt10\"><span class=\"rowText\"><textarea  class=\"inputTxt\" onchange=\"changestates()\"></textarea></span></div><div class=\"label6 rowTxt4 noBorder row3box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label7 rowTxt4 noBorder row3box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label8 rowTxt4 noBorder row3box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label9 rowTxt4 noBorder row3box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label10 rowTxt4 noBorder row3box\" onclick=\"validate(this)\"><span class=\"checkicon\" style=\"background-position:center; \"></span></div></div><div id=\"row4\"><div id=\"rowTxt11\"><span class=\"rowinTxt alignTxt\" style=\"top:32px;position:absolute;\">Level of Challenge</span></div><div id=\"rowTxt12\"><span class=\"rowinTxt2\">Substantial and sustained effort shown on a mathematical endeavor <br/>(age appropriate).</span></div><div id=\"rowTxt13\"><span class=\"rowText\"><textarea  class=\"inputTxt\" onchange=\"changestates()\"></textarea></span></div><div class=\"label6 rowTxt4 noBorder row4box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label7 rowTxt4 noBorder row4box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label8 rowTxt4 noBorder row4box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label9 rowTxt4 noBorder row4box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label10 rowTxt4 noBorder row4box\" onclick=\"validate(this)\"><span class=\"checkicon\" style=\" background-position:center; \"></span></div></div><div id=\"row5\"><div id=\"rowTxt14\"><span class=\"rowinTxt alignTxt\" style=\"top:25px;position:absolute;\">Results, Conclusions, or Answers</span></div><div id=\"rowTxt15\"><span class=\"rowinTxt2\" style=\"top:41px;position:absolute;\" >Correct and/or reasonable.</span></div><div id=\"rowTxt16\"><span class=\"rowText\"><textarea  class=\"inputTxt\" onchange=\"changestates()\"></textarea></span></div><div class=\"label6 rowTxt4 noBorder row5box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label7 rowTxt4 noBorder row5box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label8 rowTxt4 noBorder row5box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label9 rowTxt4 noBorder row5box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label10 rowTxt4 noBorder row5box\" onclick=\"validate(this)\"><span class=\"checkicon\" style=\" background-position:center; \"></span></div></div><div id=\"row6\"><div id=\"rowTxt17\"><span class=\"rowText\"><textarea style=\"width:130px;left:-4px;position:absolute;\" class=\"inputTxt\" onchange=\"changestates()\"></textarea></span></div><div id=\"rowTxt18\"><span class=\"rowText\"><textarea  style=\"width:213px;\" class=\"inputTxt\" onchange=\"changestates()\"></textarea></span></div><div id=\"rowTxt19\"><span class=\"rowText\"><textarea  class=\"inputTxt\" onchange=\"changestates()\"></textarea></span></div><div class=\"label6 rowTxt4 noBorder row6box\" onclick=\"validate(this)\"><span class=\"checkicon\"></span></div><div class=\"label7 rowTxt4 noBorder row6box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label8 rowTxt4 noBorder row6box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label9 rowTxt4 noBorder row6box\" onclick=\"validate(this)\" ><span class=\"checkicon\"></span></div><div class=\"label10 rowTxt4 noBorder row6box\" onclick=\"validate(this)\"><span class=\"checkicon\" style=\" background-position:center; \"></span></div></div></div><div class=\"foot\"></div></div></div></div>");
	
	nav = ("<div class=\"contentHolder\"><div class=\"container\"><div class=\"contentFeedback\"><div id=\"prev\"></div><div id=\"updatePage\"><span id=\"tno\" class=\"upValue\">1</span><span> of </span><span id=\"pno\" class=\"upValue\">1</span></div><div id=\"next\"></div><div id=\"del\" ></div><div class=\"btReset\" ><div class=\"icoReset\"></div></div><div class=\"btInfo\" onclick=\"openInst()\" ><div class=\"icoInfo\"></div></div><div class=\"btFeedback\" ><div class=\"icoFeed inactive\" id=\"submit\"></div></div><div class=\"score\"><div id=\"contCorrect\"><span id=\"crt\">0</span> <img src=\"images/IconCorrect.png\"></div><div id=\"contIncorrect\"><span id=\"incrt\">0</span><img src=\"images/IconIncorrect.png\"></div></div></div></div></div>")
	
	saveContainer = $('<div id="modal-container" class="save"><div class="modal-lightbox"></div><div class="modal-wrapper"><div class="modal"><div class="modal-message"></div><div class="modal-header"></div><div class="modal-body"><h3>Are you sure you want to delete this page?</h3><div class="button-container"><div class="button save-state-button"><button onclick=\"ok();\">Yes</button></div></div><div class="button-container"><div class="button cancel-button"><button onclick=\"cancel();\">No</button></div></div></div><div class="modal-footer"></div></div></div></div>');
	
	$('body').append(table[0]);
	page0.append(formContainer);
	page0.append(nav);
	page0.append(nameTxt);
	page0.append(header);
	menuContainer.append(page0);
        pageContainer.append(menuContainer);
	$('body').append(pageContainer);

	
	

$('.addicon').bind('click',function(e){
    
    
pageno++;
nextPage=pageno;
addcount++;
if (resetState==false) {
    
dataArray.push(pageno);

if (pageno==2) {
     for(i=0;i<$('.inputTxt').length;i++) {
	dataArray.push($('.inputTxt')[i].value);
    }
}else{
    for(i=0;i<$('.inputTxt').length;i++) {
	dataArray.push("");
    }
}

dataArray.push(rowSel1,rowSel2,rowSel3,rowSel4,rowSel5,rowSel6);
console.log('text input',$('.inTxt').val());
dataArray.push($('.inTxt').val());
saveEnable=true;
if (saveEnable) {
saveStageArray.push(pageno);
for(i=0;i<$('.inputTxt').length;i++) {
saveStageArray.push($('.inputTxt')[i].value);
}

saveStageArray.push(rowSel1,rowSel2,rowSel3,rowSel4,rowSel5,rowSel6);
saveStageArray.push($('.inTxt').val());
removeEndElemet=saveStageArray.length;
}
}
if (resetState==true)
  {  
    dataArray.push(pageno);


    for(i=0;i<$('.inputTxt').length;i++) {
	dataArray.push("");
    }

rowSel1=null;
    rowSel2=null;
    rowSel3=null;
    rowSel4=null;
    rowSel5=null;
    rowSel6=null;
dataArray.push(rowSel1,rowSel2,rowSel3,rowSel4,rowSel5,rowSel6);

dataArray.push("");
saveEnable=true;
if (saveEnable) {
saveStageArray.push(pageno);
for(i=0;i<$('.inputTxt').length;i++) {
	saveStageArray.push("");
    }


saveStageArray.push(rowSel1,rowSel2,rowSel3,rowSel4,rowSel5,rowSel6);

saveStageArray.push("");
removeEndElemet=saveStageArray.length;
    
}
resetState=false;
}
document.getElementById("tno").innerHTML=nextPage;
document.getElementById("pno").innerHTML=pageno;
    rowSel1=null;
    rowSel2=null;
    rowSel3=null;
    rowSel4=null;
    rowSel5=null;
    rowSel6=null;
$('.inTxt').val("");

if (dataArray.length>8) {
	nosave=false;
    }
 if (dataArray.length>pageno) {
	$('.icoReset').css({'opacity':'0.5', 'cursor':'default'});
	$('#del').css({'opacity':'1', 'cursor':'pointer'});
	$("#del").bind('click', removeElement);
	$('#next').css({'opacity':'0.5'});
	nextMoveblock=false;
	if (pageno>1){
	$('#prev').css({'opacity':'1'});
	prevMoveblock=true;
	}
       if (pageno==1) {
	$('#prev').css({'opacity':'0.5'});
	prevMoveblock=false;
	}
       
        for(i=0; i<$('.inputTxt').length;i++) {
	$('.inputTxt')[i].value="";
        }
    resetTick();
    }
    
     });

     
     
      $('#next').bind('click',function(e){
	saveEnable=false;
	if (nextMoveblock) {
	nextMoveblock=false;
          if (dataArray.length>1){
	     nextPage++;
	
	    $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	    nextBlock=true;
	    prevBlock=false;
	    if (nextPage>1) {
		$('#prev').css({'opacity':'1'});
		prevMoveblock=true;
		$('#next').css({'opacity':'1'});
		nextMoveblock=true;
		}
	    if (nextPage==1) {
		 $('#prev').css({'opacity':'0.5'});
		 prevMoveblock=false;
		
		 $('#next').css({'opacity':'0.5'});
		 nextMoveblock=false;
		
	    }
	    if (nextPage==pageno) {
		 $('#prev').css({'opacity':'1'});
		 prevMoveblock=true;
		
		 $('#next').css({'opacity':'0.5'});
		 nextMoveblock=false;
		
	    }
	    storeDatabase(nextPage);
	    document.getElementById("tno").innerHTML=nextPage;
	  
	    retriveValue();
	}
	
	
	}
    
     });
    
     
     
      $('#prev').bind('click',function(e){
	saveEnable=false;
	if (prevMoveblock) {  
	 prevMoveblock=false;
	if (dataArray.length>=1) {
	
	if (nextPage>=2) {
	     nextPage--;
	     nextBlock=false;
	     prevBlock=true;
	    
	 if (nextPage>=2) {
	    
		$('#prev').css({'opacity':'1'});
		prevMoveblock=true;
		$('#next').css({'opacity':'1'});
		nextMoveblock=true;
	
	    }
	    
	    if (nextPage<pageno){
		$('#next').css({'opacity':'1'});
		nextMoveblock=true;
	      }
	    if (nextPage==1) {
		    $('#prev').css({'opacity':'0.5'});
		    prevMoveblock=false;
	
	    }    
	   
	    storeDatabase(nextPage);
	    document.getElementById("tno").innerHTML=nextPage;
	    retriveValue();
	}
	
	
    
    }
   
     }
    });  
     
     
     
     
     
     

$('.icoReset').bind('click',function () {
       
		   var current=$(this);
		    if ($('.icoReset').css('opacity') == 1) {
			    current.removeClass('icoResetMove');
			    var to=setTimeout(function(){
				    clearInterval(to);
				    current.addClass('icoResetMove');
			    },200)
			    
			    setTimeout(function(){
			   saveEnable=false;
			    for(i=0; i<$('.inputTxt').length;i++) {
			    $('.inputTxt')[i].value="";
			    }
			    $('.icoReset').css({'opacity':'0.5', 'cursor':'default'});
			    rowSel1=rowSel2=rowSel3=rowSel4=rowSel5=rowSel6=null;
			    var resetPage=nextPage;
			    if (resetPage==1) {
				resetPage=0;
			    }else{
				resetPage = (resetPage-1)*16;
			    }
			    dataArray[resetPage]=nextPage;
			    for(i=0;i<$('.inputTxt').length;i++) {
				$('.inputTxt').value="";
				resetPage++;
			    dataArray[resetPage]=$('.inputTxt').value;
			    }
			    for(i=0;i<5;i++) {
				resetPage++;
				dataArray[resetPage]=null;
			    }
			    $('.inTxt').val("");
			    resetPage++;
			    dataArray[resetPage]="";
			    resetTick();
			    },400);
			    
			     
			    
		    }
	});
         
      /*Save Functionality*/
    eventBroker = _({}).extend(require('chaplin/lib/event_broker'));
    eventBroker.publishEvent("#fetch", { type : 'state' }, function(state) {
	    if (state) {
		    _.each(JSON.parse(state), function(value, key, list) {
			if (key == "fillDetails") {
			    savedState = value;
			
			for(i=0;i<savedState.length;i++){
			dataArray.push(savedState[i]);
			saveStageArray.push(savedState[i]);
			}
			console.log('savedState',savedState.length);
			refresh = true;
			resetState=true;
			}
			if (key == "npages") {		    
			nextPage = value;
		      document.getElementById("tno").innerHTML=nextPage;
			}
		       if (key == "tpages") {		    
			pageno = value;
			 document.getElementById("pno").innerHTML=pageno;
			 $('.icoReset').css({'opacity':'0.5', 'cursor':'default'});
			 if (pageno>nextPage) {
			    $('#prev').css({'opacity':'1'});
			    prevMoveblock=true;
			  
			    $('#next').css({'opacity':'1'});
			    nextMoveblock=true;
			  $('#del').css({'opacity':'1', 'cursor':'pointer'});
			 $("#del").bind('click', removeElement); 
			 }else if(pageno==nextPage) {
			    $('#prev').css({'opacity':'1'});
			    prevMoveblock=true;
			
			    $('#next').css({'opacity':'0.5'});
			    nextMoveblock=false;
			 $('#del').css({'opacity':'1', 'cursor':'pointer'});
			 $("#del").bind('click', removeElement); 
			 }
			 if (pageno==1) {
			    $('#prev').css({'opacity':'0.5'});
			    prevMoveblock=false;
			
			    $('#next').css({'opacity':'0.5'});
			    nextMoveblock=false;
			$('#del').css({'opacity':'0.5', 'cursor':'default'});
			 $("#del").unbind('click', removeElement); 
		
			    }
			 
			 
			 retriveValue();
			}
			
			
			
		    });
	    }
    });
    
      
      
       
      });
  
    
    function deleteElement(){
		var totlength = parseInt(dataArray.length/16);
	  if(totlength>=0){
	        if (nextPage==1) {
		    deletePos=0;
		}else{
		    deletePos=(nextPage-1) * 16;
		}
		if (nextPage>0) {
		    if(nextPage!=1)
			nextPage--;
			pageno--;
		    }
		    if (pageno==0) {
	    		pageno=1;
		    }
		    console.log('pageno delete', pageno);
		    saveEnable=false;
	     dataArray.splice(deletePos,16);
	     saveStageArray.splice(deletePos,16);
	     console.log('saveStageArray',saveStageArray);
	    document.getElementById("tno").innerHTML=nextPage;
	    document.getElementById("pno").innerHTML=pageno;
	    if (pageno==1) {
	    $('#prev').css({'opacity':'0.5'});
	    prevMoveblock=false;
	     nextMoveblock=false;
	    $('#next').css({'opacity':'0.5'});
	   $('#del').css({'opacity':'0.5', 'cursor':'default'});
	    $("#del").unbind('click', removeElement);
	    }
	    
	    
	    if (totlength==0) {
	    for(i=0; i<$('.inputTxt').length;i++) {
	    $('.inputTxt')[i].value="";
	    }
	    $('.inTxt').val("");
	    rowSel1=rowSel2=rowSel3=rowSel4=rowSel5=rowSel6=null;
	    resetTick();
	    }
	    
	    retriveValue();
	    
	    
	}
		
	    }
    
    
    
    function instruct(){
	try {
	    $('.icoInfo').addClass('icoInfoMove');
	    } catch(e) {}
	     
	    $('.question,#blocker').hide();
	    $(".icoInfo ").css({'opacity':'1','cursor':'pointer'});
    }
    
    function openInst(){
	    $('.question,#blocker').show();
	    $(".icoInfo ").css({'opacity':'0.5','cursor':'pointer'});
	    
	    
    }
    
    function toggleClassButton(element,className){
	    var currentButton=element;
	    if(!currentButton.hasClass(className)){
		currentButton.addClass(className);
	    }else{
		currentButton.removeClass(className);	
	    }
    }
    
    function validate(event){
	
	if($(event).hasClass('row1box')) {
	    rowSel1=$(event).index('.row1box');
	    $('.row1box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $(event).find('span').css({'background':'url(./images/check-on.png)', 'background-size':'contain'});
	    setrow_1=true;
	}
	
	 if($(event).hasClass('row2box')) {
	    rowSel2=$(event).index('.row2box');
	    $('.row2box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $(event).find('span').css({'background':'url(./images/check-on.png)', 'background-size':'contain'});
	    setrow_2=true;
	}
	
	if($(event).hasClass('row3box')) {
	    rowSel3=$(event).index('.row3box');
	    $('.row3box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $(event).find('span').css({'background':'url(./images/check-on.png)', 'background-size':'contain'});
	    setrow_3=true;
	}
	
	if($(event).hasClass('row4box')) {
	    rowSel4=$(event).index('.row4box');
	    $('.row4box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $(event).find('span').css({'background':'url(./images/check-on.png)', 'background-size':'contain'});
	    setrow_4=true;
	}
	
	if($(event).hasClass('row5box')) {
	    rowSel5=$(event).index('.row5box');
	    $('.row5box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $(event).find('span').css({'background':'url(./images/check-on.png)', 'background-size':'contain'});
	    setrow_5=true;
	}
	
	if($(event).hasClass('row6box')) {
	    rowSel6=$(event).index('.row6box');
	    $('.row6box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $(event).find('span').css({'background':'url(./images/check-on.png)', 'background-size':'contain'});
	    setrow_6=true;
	}
	
    $(".icoReset").css({'opacity':'1', 'cursor':'pointer'});
    }
    
    
    function retriveValue() {
    if (dataArray.length>0) {
	console.log('nextPage retrive',nextPage);
       if(nextPage==1){
       getPos = 0;
       setPos = 9;
       txtPos = 15;
       }else {
	getPos = (nextPage-1)*16;
	setPos = getPos+9;
	txtPos =getPos+15;
	
	}
	console.log('txtPos',txtPos);
       console.log('data',dataArray[txtPos]);
       if(dataArray[txtPos]!=undefined)
       $('.inTxt').val(dataArray[txtPos]);
       
       for(i=0;i<$('.inputTxt').length;i++) {
       getPos++;
       $('.inputTxt')[i].value=dataArray[getPos];
       if (dataArray[getPos]==undefined) { 
       $('.inputTxt')[i].value=""; 
       }
       
    }
    
    
    
	setTick();
	
	}
    }
    
    function setTick(){
	
	$('.row1box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	 if(dataArray[setPos]!=null){
	     $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
	$('.row1box').eq(dataArray[setPos]).find('span').css({'background':'url(./images/check-on.png) no-repeat', 'background-size':'contain'})}
	setPos++;
	
	$('.row2box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	 if(dataArray[setPos]!=null){
	    $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
	$('.row2box').eq(dataArray[setPos]).find('span').css({'background':'url(./images/check-on.png) no-repeat', 'background-size':'contain'})
	 }
	    
    setPos++;
	
	$('.row3box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	if(dataArray[setPos]!=null){
	$('.row3box').eq(dataArray[setPos]).find('span').css({'background':'url(./images/check-on.png) no-repeat', 'background-size':'contain'})
	$('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
	}
    
	setPos++;
	
	$('.row4box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	if(dataArray[setPos]!=null){
	    $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
	$('.row4box').eq(dataArray[setPos]).find('span').css({'background':'url(./images/check-on.png) no-repeat', 'background-size':'contain'})
	}
    
	setPos++;
	
	$('.row5box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	if(dataArray[setPos]!=null){
	    $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
	$('.row5box').eq(dataArray[setPos]).find('span').css({'background':'url(./images/check-on.png) no-repeat', 'background-size':'contain'})
	}
    
	setPos++;
	
	$('.row6box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	if(dataArray[setPos]!=null){
	    $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
	$('.row6box').eq(dataArray[setPos]).find('span').css({'background':'url(./images/check-on.png) no-repeat', 'background-size':'contain'})
	}
	
	saveStageArray= new Array();
    for(var v=0; v<dataArray.length; v++){
	     saveStageArray.push(dataArray[v]);
	   
	}
	console.log('retrive saveStageArray',saveStageArray);
	
    }
    
    
    
    function resetTick(){
	
	
	    $('.row1box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $('.row2box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $('.row3box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $('.row4box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $('.row5box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
	    $('.row6box').find('span').css({'background':'url(./images/check-off.png) no-repeat', 'background-size':'contain'})
    
    rowSel1=rowSel2=rowSel3=rowSel4=rowSel5=rowSel6=null;
    setrow_1=false;
    setrow_2=false;
    setrow_3=false;
    setrow_4=false;
    setrow_5=false;
    setrow_6=false;
    

    }
    
    
    eventBroker = _({}).extend(require('chaplin/lib/event_broker'));
    eventBroker.subscribeEvent('#doSave', function(state) {
	var states = {};
	/*Change here for each interactive*/
	var details = new Array();
       
	var textVal = new Array();
	var pageNext = nextPage;
	var totalPages=pageno;
       
	
       if (saveEnable) {
	
	if (refresh) {
	var temp = removeEndElemet/16;
	if (temp!=0) {
	     temp= (temp-1)*16;
	     saveStageArray.splice(temp,16);    
	}
	refresh=false;
	}
	
	  saveStageArray.push(pageno);
	    for(i=0;i<$('.inputTxt').length;i++) {
	    saveStageArray.push($('.inputTxt')[i].value);

	}
	    saveStageArray.push(rowSel1,rowSel2,rowSel3,rowSel4,rowSel5,rowSel6);
	    saveStageArray.push($('.inTxt').val());
	saveEnable=false;
      
    
       }
       
       getCurrentdata();
       
	for(var i=0; i<saveStageArray.length; i++){
	     details.push(saveStageArray[i]);
	}

    
    states = {"fillDetails":details,"npages":pageNext,"tpages":totalPages};
	/**/
	var message = {
		type : 'state',
		data : JSON.stringify(states)
	};
	eventBroker.publishEvent("#save", message);
    });
    
    function saveFunction(){
	eventBroker.publishEvent("#doSave");
    }
    
            
    function storeDatabase(refpage)
    {
    
    var resetActive = false;
    
    var refPage;
    if(nextBlock){
    
    if(refpage==1) {
	
    }
    else if(refpage==2) {
    refPage=0;
    }else{
    refPage=(refpage-2)*16;    
    }
    console.log(refPage);
    nextBlock = false;
    }

    if(prevBlock){
    console.log(refpage);
    if(refpage==1) {
    refPage=refpage*16;     
    }
    else{
    refPage=(refpage)*16;    
    }
    prevBlock=false;
    }
if(dataArray[refPage]!="")
    dataArray[refPage]=refpage;
    else
    dataArray[refPage]="";
    
    for(i=0;i<$('.inputTxt').length;i++) {
    refPage++;
    if(dataArray[refPage]!="") {
    dataArray[refPage]=dataArray[refPage];
    }else
    {
	dataArray[refPage]="";
    }
    if($('.inputTxt')[i]!="")
    {
    dataArray[refPage]= $('.inputTxt')[i].value;    
    }else{
	$('.inputTxt')[i]="";
	dataArray[refPage]="";
    }
    }
    refPage++;
    if(dataArray[refPage]!=null){
	if(setrow_1){
	dataArray[refPage]=rowSel1;
	setrow_1=false;
	}else{
	     dataArray[refPage]=dataArray[refPage];}
	     }else{
	    if(setrow_1){
		dataArray[refPage]=rowSel1;
		setrow_1=false;
	    }else{
	        dataArray[refPage]=null;
	    }
	
	
    }
    
    
    refPage++;
    if(dataArray[refPage]!=null){
	if(setrow_2){
	dataArray[refPage]=rowSel2;
	setrow_2=false;
	}else{
	     dataArray[refPage]=dataArray[refPage];}
	     }else{
	    if(setrow_2){
		dataArray[refPage]=rowSel2;
		setrow_2=false;
	    }else{
	        dataArray[refPage]=null;
	    }
	
	
    }
       
    
     refPage++;
    if(dataArray[refPage]!=null){
	if(setrow_3){
	dataArray[refPage]=rowSel3;
	setrow_3=false;
	}else{
	     dataArray[refPage]=dataArray[refPage];}
	     }else{
	    if(setrow_3){
		dataArray[refPage]=rowSel3;
		setrow_3=false;
	    }else{
	        dataArray[refPage]=null;
	    }
	
	
    }
    
     refPage++;
    if(dataArray[refPage]!=null){
	if(setrow_4){
	dataArray[refPage]=rowSel4;
	setrow_4=false;
	}else{
	     dataArray[refPage]=dataArray[refPage];}
	     }else{
	    if(setrow_4){
		dataArray[refPage]=rowSel4;
		setrow_4=false;
	    }else{
	        dataArray[refPage]=null;
	    }
	
	
    }
    
     refPage++;
    if(dataArray[refPage]!=null){
	if(setrow_5){
	dataArray[refPage]=rowSel5;
	setrow_5=false;
	}else{
	     dataArray[refPage]=dataArray[refPage];}
	     }else{
	    if(setrow_5){
		dataArray[refPage]=rowSel5;
		setrow_5=false;
	    }else{
	        dataArray[refPage]=null;
	    }
	
	
    }
    
     refPage++;
    if(dataArray[refPage]!=null){
	if(setrow_6){
	dataArray[refPage]=rowSel6;
	setrow_6=false;
	}else{
	     dataArray[refPage]=dataArray[refPage];}
	     }else{
	    if(setrow_6){
		dataArray[refPage]=rowSel6;
		setrow_6=false;
	    }else{
	        dataArray[refPage]=null;
	    }
	
	
    }
    
    
   
    refPage++;
    if(dataArray[refPage]!=undefined) {
    dataArray[refPage]=dataArray[refPage];
    }else{
	dataArray[refPage]="";
    }
    if($('.inTxt').val()!=undefined)
    {
    dataArray[refPage]= $('.inTxt').val();    
    }else{
	$('.inTxt').val("");
	dataArray[refPage]=undefined;
    } 
       
    
    console.log('store',dataArray);
    
    
    rowSel1=rowSel2=rowSel3=rowSel4=rowSel5=rowSel6=null;
    
    var temp=refpage;
    if (refpage==1) {
	temp=0;
    }else
    {
	temp = (temp-1) *16;
	
    }
    
    for (i=0;i<14;i++){
	temp++;
	if ((dataArray[temp]!="") && (dataArray[temp]!=null) && (dataArray[temp]!=undefined)) {
	    resetActive=true;
	}else{
	    resetActive=false;
	}
	
    }
    
    if (resetActive) {
	
	$('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	  
	 
    }else
    {
	 $('.icoReset').css({'opacity':'0.5', 'cursor':'default'});
	
    }
    }
    
    
   function changestates() {
	
        $('.icoReset').css({'opacity':'1', 'cursor':'pointer'});
	
    }
    
    
    
    function removeElement() {
    $("#interactive-container").append(saveContainer);
    }
    
    function ok(){
	deleteElement();
	 $("#modal-container").remove();
    }
    
    function cancel(){
	$("#modal-container").remove();
    }
    
    function onFocusOutHandler(event) {
	$('body').css({'overflow':'hidden'});
    }


    function getCurrentdata(){
	console.log('nextPage current',nextPage);
	var currentPageno=nextPage
	    if (nextPage==1) {
		currentPageno=0;
	    }else{
		currentPageno = (currentPageno-1)*16;
	    }
	
	
if(saveStageArray[currentPageno]!="")
    saveStageArray[currentPageno]=currentPageno;
    else
    saveStageArray[currentPageno]="";
    
    for(i=0;i<$('.inputTxt').length;i++) {
    currentPageno++;
    if(saveStageArray[currentPageno]!="") {
    saveStageArray[currentPageno]=saveStageArray[currentPageno];
    }else
    {
	saveStageArray[currentPageno]="";
    }
    if($('.inputTxt')[i]!="")
    {
    saveStageArray[currentPageno]= $('.inputTxt')[i].value;    
    }else{
	$('.inputTxt')[i]="";
	saveStageArray[currentPageno]="";
    }
    }
    currentPageno++;
    if(saveStageArray[currentPageno]!=null){
	if(setrow_1){
	saveStageArray[currentPageno]=rowSel1;
	setrow_1=false;
	}else{
	     saveStageArray[currentPageno]=saveStageArray[currentPageno];}
	     }else{
	    if(setrow_1){
		saveStageArray[currentPageno]=rowSel1;
		setrow_1=false;
	    }else{
	        saveStageArray[currentPageno]=null;
	    }
	
	
    }
    
    
    currentPageno++;
    if(saveStageArray[currentPageno]!=null){
	if(setrow_2){
	saveStageArray[currentPageno]=rowSel2;
	setrow_2=false;
	}else{
	     saveStageArray[currentPageno]=saveStageArray[currentPageno];}
	     }else{
	    if(setrow_2){
		saveStageArray[currentPageno]=rowSel2;
		setrow_2=false;
	    }else{
	        saveStageArray[currentPageno]=null;
	    }
	
	
    }
       
    
     currentPageno++;
    if(saveStageArray[currentPageno]!=null){
	if(setrow_3){
	saveStageArray[currentPageno]=rowSel3;
	setrow_3=false;
	}else{
	     saveStageArray[currentPageno]=saveStageArray[currentPageno];}
	     }else{
	    if(setrow_3){
		saveStageArray[currentPageno]=rowSel3;
		setrow_3=false;
	    }else{
	        saveStageArray[currentPageno]=null;
	    }
	
	
    }
    
     currentPageno++;
    if(saveStageArray[currentPageno]!=null){
	if(setrow_4){
	saveStageArray[currentPageno]=rowSel4;
	setrow_4=false;
	}else{
	     saveStageArray[currentPageno]=saveStageArray[currentPageno];}
	     }else{
	    if(setrow_4){
		saveStageArray[currentPageno]=rowSel4;
		setrow_4=false;
	    }else{
	        saveStageArray[currentPageno]=null;
	    }
	
	
    }
    
     currentPageno++;
    if(dataArray[currentPageno]!=null){
	if(setrow_5){
	saveStageArray[currentPageno]=rowSel5;
	setrow_5=false;
	}else{
	     saveStageArray[currentPageno]=saveStageArray[currentPageno];}
	     }else{
	    if(setrow_5){
		saveStageArray[currentPageno]=rowSel5;
		setrow_5=false;
	    }else{
	        dataArray[currentPageno]=null;
	    }
	
	
    }
    
     currentPageno++;
    if(saveStageArray[currentPageno]!=null){
	if(setrow_6){
	saveStageArray[currentPageno]=rowSel6;
	setrow_6=false;
	}else{
	     saveStageArray[currentPageno]=saveStageArray[currentPageno];}
	     }else{
	    if(setrow_6){
		saveStageArray[currentPageno]=rowSel6;
		setrow_6=false;
	    }else{
	        saveStageArray[currentPageno]=null;
	    }
	
	
    }
    
    
   
    currentPageno++;
    if(saveStageArray[currentPageno]!=undefined) {
    saveStageArray[currentPageno]=saveStageArray[currentPageno];
    }else{
	saveStageArray[currentPageno]="";
    }
    if($('.inTxt').val()!=undefined)
    {
    saveStageArray[currentPageno]= $('.inTxt').val();    
    }else{
	$('.inTxt').val("");
	saveStageArray[currentPageno]=undefined;
    } 
       

	
    }
    
    
//    function wrapTxt() {
//	
//	var lineWrap = $('.inputTxt').val().length;
//	if (lineWrap >= 10) {
//	console.log('aaa');
//	for (var i=0;i<=4;i++) {
//	$(('#rowTxt')+i).css({'height':'150px','border':'1px solid #000'})
//	$('#row1').css({'position':'relative','height':'150px','border':'1px solid #000'})
//	}
//	$('textarea').css({'height':'100px'})
//	}
//	
//    }




style.css
==========


@font-face{font-family:'GillSansInfant'; src:url(../fonts/font/gilsbbd.ttf)}

 
.head
{
position:absolute;
border:0px solid #000;
width:700px;
height:50px;
top:-5px;
left: 25px;
line-height:75px;
font-weight:bold;
color:#fff;
font-family:GillSansInfant;
font-size:24px;
}

.pagecon{
position:absolute;
border:0px solid #ccc;
width:300px;
height:150px;
left: 0px;
right:0px;
margin: auto;
top: 100px;
}

.title
{
position:absolute;
width:993px;
height:150px;
left: 0px;
top:0px;
background: #374938;
border-top-left-radius: 10px;
border-top-right-radius: 10px;
text-align:center;
font-weight:bold;
color:#fff;
font-family:GillSansInfant;
font-size:20px;
padding:10px;
}
.title1
{
position:absolute;
width:345px;
height:80px;
left: 0px;
top:0px;
background: #374938;
border-top-left-radius: 10px;
border-top-right-radius: 10px;
text-align:center;
font-weight:bold;
color:#fff;
font-family:GillSansInfant;
font-size:16px;
padding:10px;
}
.foot
{
position:absolute;
width:993px;
height:15px;
left: 0px;
bottom: 1px;
background: #374938;
border-bottom-right-radius: 10px;
border-bottom-left-radius: 10px;
border-bottom-right-radius: 10px;
z-index: 99;
}
#group1{
position:absolute;
border:3px solid #B2D893;
border-radius: 15px;
width:999px;
height:630px;
left: 10px;
top:60px;
background: #79AF80;
}
#droppableArea1{
position:absolute;
width:993px;
height:458px;
left: 0px;
top:150px;
background: #94bf99;
text-align: center;
overflow: hidden;
overflow-y: auto;
-webkit-overflow-scrolling: touch;
z-index: 5;
}

#close{
    position: absolute;
    top: 10px;
    right: 10px;
    font-family: GillSansInfant;
    font-size:20px;
    color: #ffffff;
    cursor: pointer;
}

/* NAV */
.contentFeedback{
	width: 1024px;
	height: 65px;
	/*background-color: rgba(47,47,47,0.5);*/
	position: absolute;
	bottom: 0;
	overflow: hidden;
        border: 0px solid #000;
}

.btFeedback,.btInfo,.btReset{
	float: right;
	width: 34px;
	height: 34px;
	cursor: pointer;
	-webkit-tap-highlight-color:rgba(0,0,0,0);
	-webkit-tap-highlight-background:<background>;
}

.btReset{margin-right:50px; opacity: 1;}
.icoReset{background-image: url('../images/btResetOn@2x.png'); background-repeat: no-repeat; opacity: .5; cursor: default; }

.icoResetMove{
	-webkit-animation: reset 1s;
}

@-webkit-keyframes reset {
	0%{
		-webkit-transform: rotate(0deg);
		background-image: url('../images/btResetOn@2x.png');
	}
	50%{
		
		background-image: url('../images/btResetOff@2x.png');
		
	}
	100%{
		-webkit-transform: rotate(-360deg);
		background-image: url('../images/btResetOn@2x.png');
	}
}

.btInfo,.btFeedback{margin-right: 17px;}

.btFeedback{
	cursor: default;
}

.icoReset,.icoFeed{
	background-position: center center;
	background-size: 100%;
	width: 35px;
	height: 37px;
}
.icoInfo{
	width: 32px;
	height: 35px;
	background-position: center center;
	background-size: 100%;
	
}

.icoInfo{background-image: url('../images/btInfoOff@2x.png');background-repeat:no-repeat;}
.icoInfoMove{background-image: url('../images/btInfoOn@2x.png');background-repeat:no-repeat;}

.icoFeed{background-image: url('../images/btFeedOff@2x.png');background-repeat:no-repeat;}
.icoFeedMove{background-image: url('../images/btFeedOn@2x.png');background-repeat:no-repeat; }

.score{
	float: right;
	height: 34px;
	width: 130px;
	border-radius: 20px;
	background-color: rgba(27,27,27,0.2);
	overflow: hidden;
	margin-right: 12px;
	display: none;
}

#contCorrect,#contIncorrect{
	width: 49%;
	height: 100%;
	/*background-color: yellow;*/
	float: left;
	text-align: center;
	vertical-align: middle;
	font-family: 'GillSans-Light';
	font-size: 18px;
	padding-top: 7px;
}

/*in case you have a lighter background you need to use this color : #177100; for #contCorrect and color: #923e3e; for #contIncorrect*/
#contCorrect{
	border-right: 1px solid rgba(0,0,0,0.3);
        color: #33ff00;
        }
#contIncorrect{
	color: #ffcbcb;
}

#contCorrect img{
	width: 17px;
	height: 18px;
}
#contIncorrect img{
	width: 15px;
	height: 17px;
}

.score div img{
	vertical-align: middle;
	margin-left: 5px;
	margin-top: -5px;
}




.txt1{
    /*font-family:GillSansInfant;*/
    text-align: center;
    margin-top:5%;
    margin-left:20%;
    width: 20%;
    height:40%;
    border-radius: 5px;
    font-size:20px;
    
}

/*input:focus*/
/*{*/
/*/*background:-webkit-radial-gradient(center,linear farthest-side,#f9c222 0,#fcdd84 100%);*/*/
/*background-image: -webkit-radial-gradient(left, rgba(200, 219, 182, 0.99), #ccc); */
/**/
/*}*/
.closeBtn{
    display: block;
    position: absolute;
    right: 20px;
    top: 10px;
    cursor: pointer;
    font-size: 16pt;
    z-index: 100;
    font-family:Icons;
}

.inst{
    position: absolute;
    right: 150px;
    bottom: 20px;
    width: 40px;
    height: 38px;
    background: url(../images/quiz_btn.png) no-repeat;
    cursor: pointer;
    
}

.question{
    display: block;
    position: absolute;
    top: -100px;
    bottom: 0px;
    width: 448px;
    height: 154px;
    border: 2px solid #7ea0c6;
    left: 0px;
    right: 0px;
    margin: auto;
    background: -moz-radial-gradient(center,circle farthest-side,#597CA5 0,#45638D 100%);
    background: -webkit-radial-gradient(center,circle farthest-side,#597CA5 0,#3D5485 100%);
    background: -webkit-gradient(radial,center center,0,center center,100%,color-stop(0%,#597CA5),color-stop(65%,#82BC54),color-stop(100%,#45638D));
    color: #fff;
    padding: 20px 35px 35px;
    font-size: 20px; 
    text-align: left;
    z-index: 2001;
    text-shadow: 0px 2px #000;
}



#blocker{
    display: block;
    position: fixed;
    width: 150%;
    height: 778px;
    left: -25%;
    top: -10px;
    background: rgba(0,0,0,0.5);
    z-index: 2000;
    
}

@font-face{font-family:'myFontfamily'; src:url(../fonts/font/GilSandsRegular.ttf)}

.nameTxt{
    position: absolute;
    right: 35px;
    top:14px;
}
.inTxt{
    width: 250px;
    height: 36px;
    border: 2px solid #B2D893;
    border-radius: 5px;
    padding: 10px;
    /*text-align: center;*/
    font-family: myFontfamily;
}
#addPage{
    width: 155px;
    height: 65px;
    /*border: 2px solid #B2D893;
    border-bottom:  2px solid #B2D893;
    border-right:  2px solid #B2D893;*/
    left: 0px;
    top: 0px;
    position: absolute;
}

#label1{
    width: 545px;
    height: 65px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  2px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 155px;
    top: 0px;
    position: absolute;
    text-align: center;
    padding: 20px;
}

#label2{
    width: 293px;
    height: 65px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  2px solid #B2D893;
    left: 700px;
    top: 0px;
    position: absolute;
    text-align: center;
    padding: 20px;
}
#label3{
    width: 155px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 0px;
    top: 65px;
    position: absolute;
    text-align: center;
    padding: 16px;
}

#label4{
    width: 249px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 155px;
    top: 65px;
    position: absolute;
     text-align: center;
    padding: 16px;
}

#label5{
    width: 296px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 404px;
    top: 65px;
    position: absolute;
     text-align: center;
    padding-top: 30px;
}
.label6{
    width: 60px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 700px;
    top: 65px;
    position: absolute;
    text-align: center;
    vertical-align: middle;
    padding-top: 30px;
}

.label7{
    width: 60px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 760px;
    top: 65px;
    position: absolute;
       text-align: center;
    padding-top: 30px;
}

.label8{
    width: 60px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 820px;
    top: 65px;
    position: absolute;
       text-align: center;
    padding-top: 30px;
}
.label9{
    width: 60px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    border-right:  2px solid #B2D893;
    left: 880px;
    top: 65px;
    position: absolute;
    text-align: center;
    padding-top: 30px;
}
.label10{
    width: 55px;
    height: 85px;
    /*border: 2px solid #B2D893;*/
    border-bottom:  4px solid #B2D893;
    left: 938px;
    top: 65px;
    position: absolute;
       text-align: center;
    padding-top: 30px;
}

.addicon{
    background: url('../images/icon.png') no-repeat;
    background-size: contain;
    position: absolute;
    width: 35px;
    height: 35px;
    border: 0px solid #000;
    left: 30px;
    top: 15px;
}
#row1{
    position: absolute;
    width: 993px;
    height: 120px;
    border: 0px solid #000;
     text-align: left;
     font-family: GillSansInfant;
     font-size: 16px;
    
}
#rowTxt1{
    width:155px;
    top:0px;
    left: 0px;
    position: absolute;
    height: 120px;
    border-top:  4px solid #B2D893;
    border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}
.rowinTxt{
    position: absolute;
    /*top: 35px;*/
    left: 15px;
}

#rowTxt2{
    width:252px;
    top:0px;
    left: 152px;
    padding: 10px;
    position: absolute;
    height: 120px;
    border-top:  4px solid #B2D893;
    border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt3{
    width:297px;
    top:0px;
    left: 403px;
    position: absolute;
    height: 120px;
    border-top:  4px solid #B2D893;
    border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}
.rowTxt4
{
top:0px;height:120px;border-top:4px solid #B2D893;border-bottom:2px solid #B2D893;
}
.alignTxt{
    position: absolute;
    left: 0px;
    right: 0px;
    margin: auto;
    text-align: center;
    vertical-align: middle;
}
.inputTxt{
    padding: 5px;
    width: 260px;
    height: 75px;
    border: 3px  solid #B2D893;
    border-radius: 9px;
    
}
.rowText
{
    padding:10px;top:2px;position:absolute;left: 8px;
    
    }
.checkicon{
    background: url('../images/check-off.png') no-repeat;
    background-size: contain;
    position: absolute;
    width: 35px;
    height: 38px;
    border: 0px solid #000;
    left: 14px;
    top: 32px;
    }
    
    #row2{
    position: absolute;
    width: 993px;
    height: 100px;
    border: 0px solid #000;
     text-align: left;
     font-family: GillSansInfant;
     font-size: 16px;
     top:120px;
    
}
#rowTxt5{
    width:155px;
    top:0px;
    left: 0px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt6{
    width:252px;
    top:0px;
    left: 152px;
    padding: 10px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt7{
    width:297px;
    top:0px;
    left: 403px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

    #row3{
    position: absolute;
    width: 993px;
    height: 100px;
    border: 0px solid #000;
     text-align: left;
     font-family: GillSansInfant;
     font-size: 16px;
     top:220px;
    
}
#rowTxt8{
    width:155px;
    top:0px;
    left: 0px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt9{
    width:252px;
    top:0px;
    left: 152px;
    padding: 10px;
    position: absolute;
    height: 100px;
       border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt10{
    width:297px;
    top:0px;
    left: 403px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}
.noBorder{
    border-top: 0px solid ;
    height: 100px;
}
    #row4{
    position: absolute;
    width: 993px;
    height: 100px;
    border: 0px solid #000;
     text-align: left;
     font-family: GillSansInfant;
     font-size: 16px;
     top:320px;
    
}
#rowTxt11{
    width:155px;
    top:0px;
    left: 0px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt12{
    width:252px;
    top:0px;
    left: 152px;
    padding: 10px;
    position: absolute;
    height: 100px;
       border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt13{
    width:297px;
    top:0px;
    left: 403px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

    #row5{
    position: absolute;
    width: 993px;
    height: 100px;
    border:0px solid #000;
     text-align: left;
     font-family: GillSansInfant;
     font-size: 16px;
     top:420px;
    
}
#rowTxt14{
    width:155px;
    top:0px;
    left: 0px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt15{
    width:252px;
    top:0px;
    left: 152px;
    padding: 10px;
    position: absolute;
    height: 100px;
       border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt16{
    width:297px;
    top:0px;
    left: 403px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

    #row6{
    position: absolute;
    width: 993px;
    height: 100px;
    border-bottom:6px solid #B2D893;
     text-align: left;
     font-family: GillSansInfant;
     font-size: 16px;
     top:520px;
    
}
#rowTxt17{
    width:155px;
    top:0px;
    left: 0px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt18{
    width:252px;
    top:0px;
    left: 152px;
    padding: 10px;
    position: absolute;
    height: 100px;
       border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#rowTxt19{
    width:297px;
    top:0px;
    left: 403px;
    position: absolute;
    height: 100px;
      border-right:2px solid #B2D893;
    border-bottom:2px solid #B2D893;
}

#prev{
    position: absolute;
    background: url('../images/btn_prev.png') no-repeat;
    background-position: center;
    left: 15px;
    top: 0px;
    width: 28px;
    height: 30px;
    opacity: 0.5;
    /*border: 1px solid #000;*/
    
}

#next{
    position: absolute;
    background: url('../images/btn_next.png') no-repeat;
    background-position: center;
    left: 111px;
    top: 0px;
    width: 28px;
    height: 30px;
    opacity: 0.5;
    /*border: 1px solid #000;*/
}

#updatePage{
    position: absolute;
    text-align: center;
    left: 42px;
    top: 5px;
    width: 70px;
    height: 30px;
    border: 0px solid #000;
    font-family: GillSansInfant;
}
#del{
    position: absolute;
    background: url('../images/page_del.png') no-repeat;
    background-position: center;
    left: 166px;
    top: 0px;
    width: 37px;
    height: 37px;
    opacity: 0.5;
     
    /*border: 1px solid #000;*/
}

.button_Box
{
position:absolute;
width:162px;
height:70px;
top:-3px;
left:-3px;
border:  3px solid #FFF380;
border-radius:15px;
/*box-shadow: 1px 1px #FFF380;*/
font-weight:normal;
font-size:18px;

}

textarea{
    resize: none;
}


