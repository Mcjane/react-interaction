# react-interaction
react-input-hidden
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="utf-8">
	<title>document</title>
	<script src="http://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/react.js"></script>
	<script src="http://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/JSXTransformer.js"></script>
</head>

<body>
<div id="container"></div>
<script type="text/jsx">
	var TestClickComponent=React.createClass({
       handleClick:function(event){
       var tipE=React.findDOMNode(this.refs.tip);
       if(tipE.style.display==='none'){
       tipE.style.display='inline';
       }else{
       tipE.style.display='none';
       }
       event.stopPropagation();
       event.preventDefault();
       },
      render:function(){
      return(
        <div>
        	<button onClick={this.handleClick}>显示|隐藏</button><span ref="tip">测试点击</span>
        </div>
      );
      }
	});
	var TestInputComponent=React.createClass({
	getInitialState:function(){
	return{
	inputContent:''
	}
	},
    changeHandler:function(event){
    this.setState({
    inputContent:event.target.value
    });
    event.preventDefault();
    event.stopPropagation();
    },
	render:function(){
    return(
    <div>
    	<input type="text" onChange={this.changeHandler}/><span>{this.state.inputContent}</span>
    </div>
    );
	}
	});
	React.render(<div><TestClickComponent/><TestInputComponent/></div>,document.getElementById('container'));
</script>

</body>
</html>
