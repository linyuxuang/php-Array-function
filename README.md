# php-Array-function

# php-ShuZu-HanShu
php常用的数组函数



数组的相关处理函数


  
    一 数组键/值操作有关的函数
	1.  array_values()  返回数组中所有的值
	2.  array_keys()    返回数组中部分的或所有的键
	3.  in_array()      检查数组中是否存在某个值
	4. array_key_exists --------》》》》》》array_key_exist() 以键为主        in_array  以值为主
	5.array_flip -- 交换数组中的键和值（如果有相同的 ‘值’ 就覆盖）
	6. array_reverse --  返回一个单元顺序相反的数组 
   
    二、 统计数组元素的个数和惟一性

    1. count() sizeof();
    2. array_count_values -- 统计数组中所有的值出现的次数
    3. array_unique -- 移除数组中重复的值

    三、使用回调函数处理数组的函数

    	1. array_filter()  用回调函数过滤数组中的单元 
	2. array_walk()   使用用户自定义函数对数组中的每个元素做回调处理




    实例： array_values()  返回数组中所有的值

             1》         $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySqL", "laguage"=>"php");

                         $arr=array_values($lamp);


                            echo '<pre>';
                            print_r($arr);
                            echo '</pre>';

                    输出：   Array
                         (
                           [0] => linux
                           [1] => Apache
                           [2] => MySqL
                           [3] => php
                         )




           2》           $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySqL", "laguage"=>"php");

                              $arr=array_values($lamp);

                              list($os, $wb, $db, $lang)=$arr;

                              echo $os."<br>";
                              echo $wb."<br>";
                              echo $db."<br>";
                              echo $lang."<br>";

                       输出：    linux
                                 Apache
                                 MySqL
                                 php       



        实例：array_keys()    返回数组中部分的或所有的键

              1》     array_keys(n1)    
              
                        $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySqL", "laguage"=>"php");

                            $arr=array_keys($lamp);

                            echo '<pre>';
                            print_r($arr);
                            echo '</pre>';


                            输出     Array
                                  (
                                      [0] => os
                                      [1] => webserver
                                      [2] => db
                                      [3] => laguage
                                  )

          2》    array_keys(n1,n2)
          
                    $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php");

                      $arr=array_keys($lamp, "MySql");

                      echo '<pre>';
                      print_r($arr);
                      echo '</pre>';

                输出    Array
                        (
                            [0] => db
                        )

       3》   array_keys(n1,n2,n3)  注意第三个参数是'布尔'如果是true，意思就是类型都得相同
  
   
                       $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100");

                            $arr=array_keys($lamp, "100", true);

                            echo '<pre>';
                            print_r($arr);
                            echo '</pre>';
   
   
     实例 in_array()      检查数组中是否存在某个值
               
                in_array(n1,n2) 
                
                       $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100", array("a", "b"));

                          if(in_array(array("a", "b"), $lamp)){
                            echo "exists";
                          }else{
                            echo "not exists";
                          }

                          echo '<pre>';
                          print_r($arr);
                          echo '</pre>';
   
                输出   exists              //如果在$lamp里面有array("a", "b") 就是true  不然就是false
   
   
   
   
                in_array(n1,n2,n3)     第三个参数检查类型是否相同
                
                $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100", array("a", "b"));

                  if(in_array(100, $lamp, true)){
                    echo "exists";
                  }else{
                    echo "not exists";
                  }
                  
                  
                 输出    not exists
   
   
   
        实例 array_key_exist()  以键为主        in_array  以值为主
   

                      $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100", array("a", "b"));

                        if(array_key_exists("os1", $lamp)){
                          echo "exists";
                        }else{
                          echo "not exists";
                        }

   
      实例 array_flip -- 交换数组中的键和值（如果有相同的 ‘值’ 就覆盖） 


     1》
                     $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100", 10=>"linux");

                        $arr=array_flip($lamp);

                        echo '<pre>';
                        print_r($arr);
                        echo '</pre>';

                  输出    Array
                        (
                            [linux] => 10
                            [Apache] => webserver
                            [MySql] => db
                            [php] => laguage
                            [100] => html
                       )

   
   
   
        实例 array_reverse()  返回一个单元顺序相反的数组
   
   
   
                     $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100", 10=>"linux");

                          $arr=array_reverse($lamp);

                          echo '<pre>';
                          print_r($arr);
                          echo '</pre>';
                          
                          
                       输出 
                            Array
                              (
                                  [0] => linux
                                  [html] => 100
                                  [laguage] => php
                                  [db] => MySql
                                  [webserver] => Apache
                                  [os] => linux
                              )
   
    
    
    
    
        统计数组元素的个数和惟一性
    
                     count就是js里面的length作用    但是在这里 第二个参数为true相当于递归作用

                         $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySql", "laguage"=>"php", "html"=>"100", 10=>"linux", array(1, 2, 3,4,5,6,7));

                         echo count($lamp, true);


    实例：array_count_values -- 统计数组中所有的值出现的次数

	 $lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySqL", "laguage"=>"php","lag"=>"php");

		$arr= array_count_values($lamp);


		echo '<pre>';
		print_r($arr);
		echo '</pre>';


		     输出    Array
				(
				    [linux] => 1
				    [Apache] => 1
				    [MySqL] => 1
				    [php] => 2
				)
   
   
   
        实例： array_unique    移除数组中重复的值

   
			$lamp=array("os"=>"linux", "webserver"=>"Apache", "db"=>"MySqL", "laguage"=>"php","lag"=>"php");

			$arr= array_unique($lamp);


			echo '<pre>';
			print_r($arr);
			echo '</pre>';
			   输出
				Array
				(
				    [os] => linux
				    [webserver] => Apache
				    [db] => MySqL
				    [laguage] => php
				)

   
使用回调函数处理数组的函数


        实例：array_filter    用回调函数过滤数组中的单元 

		 1》

				  $arr=array(1,2,3,4,5,-6,7,7,8,8,-9,9,10,11,-12);

				       $arr1=array_filter($arr, "myfun");

					function myfun($n){
					  if($n>0)
					    return true;
					  else
					    return false;
					}

				      echo '<pre>';
				      print_r($arr1);
				      echo '</pre>';


				    输出            Array
						(
						    [0] => 1
						    [1] => 2
						    [2] => 3
						    [3] => 4
						    [4] => 5
						    [6] => 7
						    [7] => 7
						    [8] => 8
						    [9] => 8
						    [11] => 9
						    [12] => 10
						    [13] => 11
						)


		   2》

				$arr=array(1,2,3,4,5,-6,7,7,8,8,-9,9,10,11,-12);


				     $arr1=array_filter($arr, "myfun");

				      function myfun($n){
					if($n%2==0)
					  return true;
					else
					  return false;
				      }


				    echo '<pre>';
				    print_r($arr1);
				    echo '</pre>';

			    输出     Array
					(
					    [1] => 2
					    [3] => 4
					    [5] => -6
					    [8] => 8
					    [9] => 8
					    [12] => 10
					    [14] => -12
					)



    实例 ：array_walk    使用用户自定义函数对数组中的每个元素做回调处理
                        
	 array_walk(n1,n2)
			 
		1》	 
				$lamp=array("os"=>"linux", "wb"=>"apache", "db"=>"mysql", "la"=>"php");

					array_walk($lamp, "myfun1");

					function myfun1($value, $key){
						echo "The key '{$key}' has the value '$value' <br>";
					}

						 输出        The key 'os' has the value 'linux' 
							      The key 'wb' has the value 'apache' 
							      The key 'db' has the value 'mysql' 
							      The key 'la' has the value 'php' 
 



       array_walk(n1,n2,n3)


		2》		$lamp=array("os"=>"linux", "wb"=>"apache", "db"=>"mysql", "la"=>"php");

					array_walk($lamp, "myfun1", "========");

					function myfun1($value, $key, $p){
						echo "The key '{$key}' has {$p}  '$value' <br>";
					}
                                        输出

						The key 'os' has ======== 'linux' 
						The key 'wb' has ======== 'apache' 
						The key 'db' has ======== 'mysql' 
						The key 'la' has ======== 'php' 




               3》
				$lamp=array("os"=>"linux", "wb"=>"apache", "db"=>"mysql", "la"=>"php");
				$lp=array("os"=>"window", "wb"=>"apache", "db"=>"oracle", "la"=>"php");


					$arr=array_map("myfun1", $lamp, $lp);

					function myfun1($n, $t){
						if($n==$t){
							return "相同的";
						}

						return "不相同的";
					}

				echo '<pre>';
				print_r($arr);
				echo '</pre>';
		    输出		
				  Array
				(
				    [0] => 不相同的
				    [1] => 相同的
				    [2] => 不相同的
				    [3] => 相同的
				)
				
				
				
				
				

		数组的排序函数
		    sort()   对数组排序
		    
		    rsort()  对数组逆向排序
		    
		    usort()  使用用户自定义的比较函数对数组中的值进行排序 
		    
		    asort()    对数组进行排序并保持索引关系
		    
		   arsort()   对数组进行逆向排序并保持索引关系 
		   
		    uasort()  使用用户自定义的比较函数对数组中的值进行排序并保持索引关联 
		    
		     ksort()  对数组按照键名排序
		     
		    krsort()   对数组按照键名逆向排序
		    
		    uksort()   使用用户自定义的比较函数对数组中的键名进行排序 
		    
		    natsort()   用"自然排序"算法对数组排序 
		  
		    natcasesort()  用"自然排序"算法对数组进行不区分大小写字母的排序
		    array_multisort()

		     1. 简单的数组排序
		     sort() rsort()
		     
		    2. 根据键名对数组排序
			ksort() krsort()
			
		   3. 根据元素的值对数组排序
		      asort() arsort()
		      
		   4. 根据“自然数排序”法对数组排序
			natsort()  natcasesort()
			
		    5. 根据用户自定义规则对数组排序
		      usort() uasort() uksort()
		      
		    6.多维数组的排序
		     array_multisort

		 * 拆分、合并、分解、接合的数组函数
		 
		   1. array_slice()   从数组中取出一段
		   
		   2.array_splice()     把数组中的一部分去掉并用其它值取代 

		   3. array_combine();   创建一个数组，用一个数组的值作为其键名，另一个数组的值作为其值
		   
		   4. array_merge();    合并一个或多个数组
		   
		   5. array_intersect();  计算数组的交集
		   
		   6. array_diff()      计算数组的差集

		 * 数组与数据结构的函数
		 
		     1. 使用数据实现堆栈
			 array_push()   将一个或多个单元压入数组的末尾（入栈） 

			 array_pop()   将数组最后一个单元弹出（出栈）

		     2. 使用队列
			  array_unshift()   在数组开头插入一个或多个单元
			  
			  array_shift()     将数组开头的单元移出数组 

			  unset()     销毁变量

		   其它与数据操作有关的函数 

		       array_rand();    从数组中随机取出一个或多个单元 
		       
		       shuffle()         将整个数组的值打乱随机生成
		       
		       array_sum()      计算数组中所有值的和 
		       
		       range()      


  sort()   对数组排序 
              
	      
	   1》          $fruits = array(1=>"lemon", 8=>"orange",3=> "banana",6=>"apple");

			    sort( $fruits);
			    foreach($fruits as $key =>$val){
				    echo $key.'===>'.$val.'<br/>';
			     }

				     输出        0===>apple
						1===>banana
						2===>lemon
						3===>orange




				   2》                   
						   $fruits = array(1, 8,3,6);
						    sort( $fruits);
						    foreach($fruits as $val){
							    print_r($val.'<br>');
						     }

						      输出      1
								3
								6
								8


  rsort()  对数组逆向排序
  
                               $fruits = array(1, 8,3,6);
			        rsort( $fruits);
			      
			     foreach($fruits as $val){
				echo '<pre>';
				    print_r($val);
				   echo '</pre>';
			      }

			    输出        8
					6
					3
					1
					
					
					
  usort — 使用用户自定义的比较函数对数组中的值进行排序 
  

				function cmp($a, $b)
				{
				    if ($a == $b) {
					return 0;
				    }
				    return ($a < $b) ? -1 : 1;
				}

				$a = array(3, 2, 5, 6, 1);

				usort($a, "cmp");

				foreach ($a as $value) {
				    echo "$value\n";
				}

                          输出   1 2 3 5 6

asort  对数组进行排序并保持索引关系


           $fruits = array("d" => "1", "a" => "4", "b" => "6", "c" => "2");
			asort($fruits);
			foreach ($fruits as $key => $val) {
			    echo "$key = $val\n";
			}

                输出  d = 1   c = 2   a = 4   b = 6
   
   
   
arsort — 对数组进行逆向排序并保持索引关系 

		   $fruits = array("d" => "2", "a" => "5", "b" => "7", "c" => "1");
			arsort($fruits);
			foreach ($fruits as $key => $val) {
			    echo "$key = $val\n";
			}

		 输出   b = 7 a = 5 d = 2 c = 1



uasort — 使用用户自定义的比较函数对数组中的值进行排序并保持索引关联 

		   function text($a,$b){
			if($a==$b){
				return 0;
			}else{
				return ($a<$b)?-1:1;
			}
		   }

		 $arr=array(1,3,2,5,7,6);
		 uasort($arr,'text');

		 foreach($arr as $key=>$val){
			echo $key.'==>'.$val.'<br>';
		 }


		  输出           0==>1
				2==>2
				1==>3
				3==>5
				5==>6
				4==>7


   
 ksort  对数组按照键名排序

   
			$arr=array(1=>'a1',3=>'a3',2=>'a2',5=>'a5',7=>'a7',6=>'a6');
			  ksort($arr);

			 foreach($arr as $key=>$val){
				echo $key.'==>'.$val.'<br>';
			 }

			   输出 1==>a1
				2==>a2
				3==>a3
				5==>a5
				6==>a6
				7==>a7

   
   
   krsort — 对数组按照键名逆向排序


				 $arr=array(1=>'a1',3=>'a3',2=>'a2',5=>'a5',7=>'a7',6=>'a6');
				  krsort($arr);

				 foreach($arr as $key=>$val){
					echo $key.'==>'.$val.'<br>';
				 }

				  输出          7==>a7
						6==>a6
						5==>a5
						3==>a3
						2==>a2
						1==>a1
						
						
						
uksort — 使用用户自定义的比较函数对数组中的键名进行排序						
						
					 function text($a1,$b1){
						if($a1==$b1){
							return 0;
						}else{
							return ($a1<$b1)?-1:1;
						}
					 }

					 $arr=array(1=>'a1',3=>'a3',2=>'a2',5=>'a5',7=>'a7',6=>'a6');
					  uksort($arr,'text');

					 foreach($arr as $key=>$val){
						echo $key.'==>'.$val.'<br>';
					 }

					   输出     1==>a1
							2==>a2
							3==>a3
							5==>a5
							6==>a6
							7==>a7					
						
						
						
natsort — 用"自然排序"算法对数组排序 

		                1》对自然数‘ 字母的排序’						
							
						$a=array('a','j','b','l','o');

						print_r($a);
						natsort($a);
						print_r($a);
						
				输出   
						    Array
							(
							    [0] => a
							    [1] => j
							    [2] => b
							    [3] => l
							    [4] => o
							)

							Array
							(
							    [0] => a
							    [2] => b
							    [1] => j
							    [3] => l
							    [4] => o
							)


		2》 对数字的排序
		              
		                    $a=array(2,6,8,1,0,4,5);
					print_r($a);
					natsort($a);
					print_r($a);

					输出       Array
							(
							    [0] => 2
							    [1] => 6
							    [2] => 8
							    [3] => 1
							    [4] => 0
							    [5] => 4
							    [6] => 5
							)
							Array
							(
							    [4] => 0
							    [3] => 1
							    [0] => 2
							    [5] => 4
							    [6] => 5
							    [1] => 6
							    [2] => 8
							)

						
natcasesort — 用"自然排序"算法对数组进行不区分大小写字母的排序 						


                                 $array2=array('IMG0.png', 'img12.png', 'img10.png', 'img2.png', 'img1.png', 'IMG3.png');

							print_r($array2);


							natcasesort($array2);
							print_r($array2);

						输出    Array
								(
								    [0] => IMG0.png
								    [1] => img12.png
								    [2] => img10.png
								    [3] => img2.png
								    [4] => img1.png
								    [5] => IMG3.png
								)
								Array
								(
								    [0] => IMG0.png
								    [4] => img1.png
								    [3] => img2.png
								    [5] => IMG3.png
								    [2] => img10.png
								    [1] => img12.png
								)


array_multisort — 对多个数组或多维数组进行排序


						 SORT_ASC - 按照上升顺序排序
						 SORT_DESC - 按照下降顺序排序 
						  
						  
						 ◦SORT_REGULAR - 将项目按照通常方法比较 
						 ◦SORT_NUMERIC - 将项目按照数值比较 
						 ◦SORT_STRING - 将项目按照字符串比较 


                     SORT_ASC与SORT_DESC的用法》》》》
						$ar1 = array(10, 100, 100, 0);
						$ar2 = array(1, 3, 2, 4);
						array_multisort($ar1,SORT_ASC , $ar2,SORT_DESC);
						//升顺序排序
						print_r($ar1);
						//降顺序排序
						print_r($ar2);


						Array
						(
						    [0] => 0
						    [1] => 10
						    [2] => 100
						    [3] => 100
						)
						Array
						(
						    [0] => 4
						    [1] => 1
						    [2] => 3
						    [3] => 2
						)


				几种合起来用法
					 ◦SORT_NUMERIC - 将项目按照数值比较 ◦
					 SORT_STRING - 将项目按照字符串比较 

					 SORT_ASC - 按照上升顺序排序
					 SORT_DESC - 按照下降顺序排序 
					
					$arr=array(1,3,2,6,5,8,7,'90');
					$arr1=array(1,3,2,6,5,8,7,'90');
					 array_multisort($arr,SORT_ASC,SORT_STRING,

					 $arr1,SORT_ASC,SORT_NUMERIC);

					 var_dump($arr);


					var_dump($arr1);


			                           输出    
							  array(8) {
								  [0]=>
								  int(1)
								  [1]=>
								  int(2)
								  [2]=>
								  int(3)
								  [3]=>
								  int(5)
								  [4]=>
								  int(6)
								  [5]=>
								  int(7)
								  [6]=>
								  int(8)
								  [7]=>
								  string(2) "90"
								}
							 array(8) {
								  [0]=>
								  int(1)
								  [1]=>
								  int(2)
								  [2]=>
								  int(3)
								  [3]=>
								  int(5)
								  [4]=>
								  int(6)
								  [5]=>
								  int(7)
								  [6]=>
								  int(8)
								  [7]=>
								  string(2) "90"
								}
 * 拆分、合并、分解、接合的数组函数
 
 

             array_slice — 从数组中取出一段    可选参数(第四个参数true代表显示原来的下标) 默认：重新分配下标


				    $lamp=array("Linux", "Apache", "MySQL", "PHP");


				     print_r(array_slice($lamp,1,2));

					echo '<br>';
				      print_r(array_slice($lamp,-2,1 ,true));


                              输出      Array ( [0] => Apache [1] => MySQL ) 
                                        Array ( [2] => MySQL )


                 array_splice()     把数组中的一部分去掉并用其它值取代 
		 
		 
		        $a1=array("a"=>"red","b"=>"green","c"=>"blue","d"=>"yellow");
			$a2=array("b"=>"orange");
			array_splice($a1,0,2,$a2);
			print_r($a1);
		 
		 
		      输出    Array ( [0] => orange [b] => green [c] => blue [d] => yellow )
		      
		      
		      
	         array_combine — 创建一个数组，用一个数组的值作为其键名，另一个数组的值作为其	      
		      
		         $a=array('a','b','c','d');
			 $b=array('a1','b1','c1','d1');
			  print_r(array_combine($a,$b));

			   输出  Array ( [a] => a1 [b] => b1 [c] => c1 [d] => d1 )
			   
			   
			   
			   
        array_merge — 合并一个或多个数组


			  $a1=array("OS", "WebServer", "DataBase", "Language",1,3,4,5,6,78);
			 $a2=array("Linux", "Apache", "MySQL", "PHP",5,78); 


			  $a3=array_merge($a1,$a2);
			 print_r($a3);

			  输出    
			Array
			(
			    [0] => OS
			    [1] => WebServer
			    [2] => DataBase
			    [3] => Language
			    [4] => 1
			    [5] => 3
			    [6] => 4
			    [7] => 5
			    [8] => 6
			    [9] => 78
			    [10] => Linux
			    [11] => Apache
			    [12] => MySQL
			    [13] => PHP
			    [14] => 5
			    [15] => 78
			)



	     array_intersect — 计算数组的交集
	  
		 $a=array(1,2,3,4,5,6);
                 $b=array(1,'a',6);
      
                  print_r(array_intersect($a,$b));      
		      
		   输出     Array ( [0] => 1 [5] => 6 )
		      
		      
		      
		 
	      array_diff — 计算数组的差集


		   $a=array(1,2,3,4,5,6,'a');
		   $b=array(1,'a',6);

		   print_r(array_diff($a,$b));


		    输出   Array ( [1] => 2 [2] => 3 [3] => 4 [4] => 5 )	
		    

* 数组与数据结构的函数

		        1. 使用数据实现堆栈
			
			
			     array_push()   将一个或多个单元压入数组的末尾（入栈）
		 
		                  $a=array(6,'a');
				   $b=array(1,'a',6);

				  array_push($a,$b);
				  print_r($a);


				    输出    Array
						(
						    [0] => 6
						    [1] => a
						    [2] => Array
							(
							    [0] => 1
							    [1] => a
   							    [2] => 6
							)

						)

		  array_pop — 将数组最后一个单元弹出（出栈）

                                   $a=array(1,2,3,5);
				   array_push($a,1,0,9);
				   $val= array_pop($a);
				   print_r($a);
				   print_r($val);


				  输出    Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 5 [4] => 1 [5] => 0 )     9
				  
		 
		array_unshift — 在数组开头插入一个或多个单元 

                              
			   $a=array(1,2,3,5);
			   array_unshift($a,'w',0,9);

			   print_r($a);

			   输出   Array
					(
					    [0] => w
					    [1] => 0
					    [2] => 9
					    [3] => 1
					    [4] => 2
					    [5] => 3
					    [6] => 5
					)

		 
		 array_shift — 将数组开头的单元移出数组   第二个参数代表‘一次获取两个数组里面的元素的随机数’


				   $a=array(1,2,3,5);
				   array_shift($a);

				   print_r($a);

				   输出   Array
						(
						    [0] => 2
						    [1] => 3
						    [2] => 5
						)

		 
		 array_rand  获取数组里面元素的随机数
		 
		      $a=array(1,2,3,4,5,6,7,8,9);
			    $b=array_rand($a);
			     print_r($b);


			       或
			       $a=array(1,2,3,4,5,6,7,8,9);
				    $b=array_rand($a,2);
				     print_r($b);
			     
		shuffle 将整个数组的值打乱随机生成 
			     
	         $arr=array(1,3,4,5,76,7,98,5,9,4,3,3,2,2,22,21);

			shuffle($arr); 

			print_r($arr);
			
			
               array_sum — 计算数组中所有值的和 

                   $arr=array(1,3,4,5,76,7,98,5,9,4,3,3,2,2,22,21);

	             echo array_sum($arr); 
		     

      range — 建立一个包含指定范围单元的数组
      
       这里又三个参数，第一个代表数组元素最小从0开始，第二个参数代表数组元素最大数，第三个参数代表每个数组元素递增10


					$arr=range(0,50,10);

					  print_r($arr);

			       输出
					Array
					(
					    [0] => 0
					    [1] => 10
					    [2] => 20
					    [3] => 30
					    [4] => 40
					    [5] => 50
					)








