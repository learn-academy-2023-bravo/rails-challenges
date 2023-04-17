3.0.0 :001 > Account.all
  Account Load (1.3ms)  SELECT "accounts".* FROM "accounts"
 =>                                                            
[#<Account:0x00007fb129b88e18                                  
  id: 1,                                                       
  username: "bobby bob",                                       
  password: "[FILTERED]",                                      
  email: "yahoo@yahoo",                                        
  created_at: Mon, 17 Apr 2023 21:02:30.113780000 UTC +00:00,  
  updated_at: Mon, 17 Apr 2023 21:02:30.113780000 UTC +00:00>, 
 #<Account:0x00007fb126ff2038                                  
  id: 2,                                                       
  username: "bobby bob bob",                                   
  password: "[FILTERED]",                                      
  email: "bobby@yahoo.com",                                    
  created_at: Mon, 17 Apr 2023 21:10:42.761614000 UTC +00:00,  
  updated_at: Mon, 17 Apr 2023 21:10:42.761614000 UTC +00:00>,
 #<Account:0x00007fb126ff1ea8
  id: 3,
  username: "bobby bob bo211b",
  password: "[FILTERED]",
  email: "4324bobby@yahoo.c\nom",
  created_at: Mon, 17 Apr 2023 21:30:07.495795000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 21:30:07.495795000 UTC +00:00>,
 #<Account:0x00007fb126ff1d18
  id: 4,
  username: "marky mar4k",
  password: "[FILTERED]",
  email: "ma4rk@yahoo.com",
  created_at: Mon, 17 Apr 2023 21:57:08.825135000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 21:57:08.825135000 UTC +00:00>] 
3.0.0 :002 > Addy.all
/Users/learnacademy/.rvm/gems/ruby-3.0.0/gems/activemodel-7.0.4.3/lib/active_model/validations/validates.rb:110:in `validates': You need to supply at least one attribute (ArgumentError)
3.0.0 :003 > Addy.all
  Addy Load (1.1ms)  SELECT "addies".* FROM "addies"
 =>                                                
[#<Addy:0x00007fb125e4ab00                         
  id: 1,                           
  street: "juniper",               
  street_number: nil,              
  city: nil,                       
  state: nil,                      
  zip: nil,                        
  account_id: 1,                   
  created_at: Mon, 17 Apr 2023 21:35:32.410200000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 21:35:32.410200000 UTC +00:00>,
 #<Addy:0x00007fb12c20b4a0
  id: 2,
  street: "Juniperrr",
  street_number: "12354",
  city: "SD",
  state: "CA",
  zip: 9322105,
  account_id: 1,
  created_at: Mon, 17 Apr 2023 22:49:13.744233000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 22:49:13.744233000 UTC +00:00>,
 #<Addy:0x00007fb12c20b3d8
  id: 3,
  street: "Juniperrr",
  street_number: "12354",
  city: "SD",
  state: "CA",
  zip: 93,
  account_id: 2,
  created_at: Mon, 17 Apr 2023 22:49:50.723228000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 22:49:50.723228000 UTC +00:00>,
 #<Addy:0x00007fb12c20b310
  id: 4,
  street: "Juniperrr",
  street_number: "12354",
  city: "SD",
  state: "CA",
  zip: 93,
  account_id: 2,
  created_at: Mon, 17 Apr 2023 22:50:14.872908000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 22:50:14.872908000 UTC +00:00>,
 #<Addy:0x00007fb12c20b248
  id: 5,
  street: "Juniperrr",
  street_number: "12354",
  city: "SD",
  state: "CA",
  zip: 93,
  account_id: 2,
  created_at: Mon, 17 Apr 2023 22:50:19.632040000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 22:50:19.632040000 UTC +00:00>,
 #<Addy:0x00007fb12c20b180
  id: 6,
  street: "Juniperrr",
  street_number: "12354",
  city: "SD",
  state: "CA",
  zip: 93,
  account_id: 2,
  created_at: Mon, 17 Apr 2023 22:53:14.494733000 UTC +00:00,
  updated_at: Mon, 17 Apr 2023 22:53:14.494733000 UTC +00:00>] 
3.0.0 :004 > 
