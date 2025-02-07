# PHP-DOMDocument
php domdocument with bangladesh stock exchange plc get public data

       <?php
      
        $html= file_get_contents('https://bongotechbd.xyz/crypto/simple_crypto.html');
        
        libxml_use_internal_errors(true);
        $dom=new DOMDocument;
        $dom-> loadHTML($html);
        
        $xpath=new DOMXpath($dom);
         
         $values= $xpath-> query ('//div[contains(@class, "scroll-item")]//a');
         
         foreach($values as $item){
      	   
      	   
      	   
      	   $text=$item->textContent;
      	   $cleaned = preg_replace('/[^\x20-\x7E]/', ' ', $text);
      	   $cleaned = preg_replace('/[\p{Zs}]+/u', ' ', $cleaned); 
      	   $td= trim($cleaned);
      	   
      	   
      	   $parts=explode(' ',$td);
      	   
      	   if(count($parts)>=4){
      		   
      		   $name= $parts[0];
      		   $price= $parts[1];
      		   $change= $parts[2];
      		   $persent= $parts[3];
      		   
      		   
      		    echo 'Name : ' .$name . '<br>';
      		    echo 'price : ' .$price . '<br>';
      		    echo 'change : ' .$change . '<br>';
      		    echo 'persent : ' .$persent . '<br>';
      		   
      	   }
      	   echo "<br>";
         }
      
      ?>
