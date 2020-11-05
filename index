const axios = require('axios');
exports.handler = async  function(context, event, callback) {
try {
const {CurrentTask} = event;
console.log(CurrentTask);

  // calling task handlers
  switch(CurrentTask){
    case 'greeting' : 
      await FunctionCaller("greetingTaskHandler",context, event, callback);      
      break;

    case 'phone_check':      
      await FunctionCaller("phoneCheckTaskHandler",context, event, callback);
      break;

    case 'account_check':
       await FunctionCaller("accountCheckTaskHandler",context, event, callback);
      break;

    case 'agent_transfer':
      await FunctionCaller("agentTransferHandler",context, event, callback);
      break;

    case 'yes_no':
      await FunctionCaller("yesNoHandler",context, event, callback);
      break;
        
    case 'goodbye' :
      await FunctionCaller("goodbyeTaskHandler",context, event, callback);
      break;

    case 'collect_fallback' :
      await FunctionCaller("collectFallbackTaskHandler",context, event, callback);
      break;

    case 'fallback' :
      await FunctionCaller("fallbackHandler",context, event, callback);
      break;

    default :
       await FunctionCaller("fallbackHandler",context, event, callback);
      break;
  } 
  } catch (error) {
    console.error(error);    
    callback( error);
  }
};

// This function to call other function
 const FunctionCaller= async (functionName,context, event, callback) =>{
   var FunctionURL= context.fnURL+functionName
      console.log(FunctionURL);           
      axios.post(FunctionURL, event, {headers: { 'Content-Type': 'application/json'} })
        .then(response => { callback(null, response.data); })
        .catch(error => {       
              var errorresult={"Status":error.message};
      console.log(error.message);
      callback(null,errorresult);});
 } 
 
