&lt;?xml version="1.0" encoding="UTF-8"?&gt; &nbsp;<br />
&lt;configuration&gt; &nbsp;<br />
&nbsp; &lt;system.webServer&gt; &nbsp;<br />
&lt;handlers&gt;&nbsp;<br />
&nbsp; &nbsp; &lt;remove name="PHP54_via_FastCGI" /&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;add name="PHP54_via_FastCGI" path="*.php"<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;verb="GET, PUT, POST, DELETE, HEAD"&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;modules="FastCgiModule"&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;scriptProcessor="D:\Program Files (x86)\PHP\v5.4\php-cgi.exe"<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;resourceType="Either" requireAccess="Script" /&gt;<br />
&nbsp; &nbsp; &lt;/handlers&gt;<br />
&lt;staticContent&gt;<br />
&lt;mimeMap fileExtension=".woff" mimeType="font/x-woff" /&gt;<br />
&nbsp; &nbsp; &lt;/staticContent&gt;<br />
&nbsp; &nbsp; &lt;rewrite&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &lt;rules&gt; &nbsp;<br />
&lt;rule name="rD"&gt;<br />
&lt;match url="^$" /&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Index_indexStar" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rD1"&gt;<br />
&lt;match url="^(.?)btag=(.+)_(.+)_(.+)$" /&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Index_indexStar_btag_{R:2}_{R:3}_{R:4}" appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 2j"&gt;<br />
&lt;match url="^ClickId=(.+)$" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Index_IndexStar_ClickId_{R:1}" &nbsp;appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 3j"&gt;<br />
&lt;match url="^api/v2/setBonusStatus" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_setBonusStatus" &nbsp;appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 4j"&gt;<br />
&lt;match url="^api/v2/levelupgrade" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Score_changeLevel" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 5j"&gt;<br />
&lt;match url="^api/v2/scoreexchange" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Score_changeWallet" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 6j"&gt;<br />
&lt;match url="^api/v2/relemail" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=User_sendverify" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 7j"&gt;<br />
&lt;match url="^api/v2/mobile/relemail" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=User_sendverify" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 8j"&gt;<br />
&lt;match url="^api/v2/mobile/setBonusStatus" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_setBonusStatus" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 9j"&gt;<br />
&lt;match url="^api/v2/mobile/levelupgrade" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Score_changeLevel" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 10j"&gt;<br />
&lt;match url="^api/v2/mobile/scoreexchange" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Score_changeWallet" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 11j"&gt;<br />
&lt;match url="^api/v2/jackpots" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=/Index_HapiJackpots" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 12j"&gt;<br />
&lt;match url="^api/v2/mobile/cms/about" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Mobile_about" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 13j"&gt;<br />
&lt;match url="^api/v2/user/settings" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_getAutoBonus" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 14j"&gt;<br />
&lt;match url="^api/v2/mobile/faq" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Mobile_faq" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 15j"&gt;<br />
&lt;match url="^api/v2/mobile/cms/bonus-(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 17j"&gt;<br />
&lt;match url="^api/v2/cms/bonus-(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 18j"&gt;<br />
&lt;match url="^api/v2/cms/invoice-(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_showInvoice_id_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 19j"&gt;<br />
&lt;match url="^api/v2/mobile/cms/invoice-(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_showInvoice_id_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 20j"&gt;<br />
&lt;match url="^api/v2/cms/about-bonuses" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_about-bonuses-desktop" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 21j"&gt;<br />
&lt;match url="^api/v2/mobile/cms/terms" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_termsconditions" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 22j"&gt;<br />
&lt;match url="^api/v2/cms/terms" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_termsconditions" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 23j"&gt;<br />
&lt;match url="^api/v2/cms/refundPolicy" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_refundPolicy" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 24j"&gt;<br />
&lt;match url="^api/v2/cms/responsible-gaming" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_responsiblegambling" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 25j"&gt;<br />
&lt;match url="^api/v2/mobile/cms/responsible-gaming" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_page_label_responsiblegambling" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 26j"&gt;<br />
&lt;match url="^api/v2/cms/about" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_about" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 27j"&gt;<br />
&lt;match url="^api/v2/games" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_games" appendQueryString="false" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 16j"&gt;<br />
&lt;match url="^api/v2/mobile/games" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Mobile_games" &nbsp;appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
<br />
&lt;rule name="rule 28j"&gt;<br />
&lt;match url="^api/v2/cms/campaigns" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_campaigns" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 29j"&gt;<br />
&lt;match url="^api/v2/faq" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_faqs" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 30j"&gt;<br />
&lt;match url="^api/v2/mobile/auth" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_HappistarLogin" &nbsp;appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 31j"&gt;<br />
&lt;match url="^api/v2/auth" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_HappistarLogin" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 32j"&gt;<br />
&lt;match url="^api/v2/mobile/user/password" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_MobileChangePassword" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 33j"&gt;<br />
&lt;match url="^api/v2/user/password" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_MobileChangePassword" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 34j"&gt;<br />
&lt;match url="^api/v2/mobile/bootstrap" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_MobileBootstrap" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 35j"&gt;<br />
&lt;match url="^api/v2/bootstrap" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Index_DesktopBootstrap" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 36j"&gt;<br />
&lt;match url="^api/v2/mobile/playforfun/(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Mobile_play_gameid_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 37j"&gt;<br />
&lt;match url="^api/v2/playforfun/(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_play_gameid_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 38j"&gt;<br />
&lt;match url="^api/v2/mobile/play/(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Mobile_playGame_gameid_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 39j"&gt;<br />
&lt;match url="^api/v2/play/(.+)" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Desktop_playGame_gameid_{R:1}" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 44j"&gt;<br />
&lt;match url="^api/v2/signup/(.+)/register" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_register_userId_{R:1}" appendQueryString="false" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 45j"&gt;<br />
&lt;match url="^api/v2/mobile/signup/(.+)/register" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_register_userId_{R:1}" &nbsp;appendQueryString="false" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
<br />
<br />
&lt;rule name="rule 42j"&gt;<br />
&lt;match url="^api/v2/mobile/custom/isUsernameDuplicate" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_isUsernameDuplicate" &nbsp;appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 43j"&gt;<br />
&lt;match url="^api/v2/custom/isUsernameDuplicate" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_isUsernameDuplicate" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
<br />
&lt;rule name="rule 40j"&gt;<br />
&lt;match url="^api/v2/mobile/custom/isEmailAddressAvailable" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_isEmailAddressAvailable" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 41j"&gt;<br />
&lt;match url="^api/v2/custom/isEmailAddressAvailable" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_isEmailAddressAvailable" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
<br />
<br />
&lt;rule name="rule 46j"&gt;<br />
&lt;match url="^api/v2/signup" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_signup" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 47j"&gt;<br />
&lt;match url="/moneyPage/neteller" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_MobileNetellerPage" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 48j"&gt;<br />
&lt;match url="^api/v2/mobile/payment/deposit" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_HapiDepositMobile" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 49j"&gt;<br />
&lt;match url="^api/v2/payment/deposit/methods" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_methods" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 50j"&gt;<br />
&lt;match url="^api/v2/payment/deposit" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_HapiDeposit" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 51j"&gt;<br />
&lt;match url="/Desktop/neteller" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_DesktopNetellerPage" appendQueryString="false" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 52j"&gt;<br />
&lt;match url="^api/v2/user/metrics" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_metrics" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 53j"&gt;<br />
&lt;match url="^api/v2/mobile/user/metrics" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_metrics" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 54j"&gt;<br />
&lt;match url="/moneyPage/CreditCard" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_MobileCreditCardPage" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 55j"&gt;<br />
&lt;match url="/Desktop/CreditCard" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=MoneyIn_DesktopCreditCardPage" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 56j"&gt;<br />
&lt;match url="^api/v2/user/transactions/game" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=HappistarRecord_game" &nbsp; /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 57j"&gt;<br />
&lt;match url="^api/v2/user/transactions/account" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Xianjin_MobileXianjin" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 58j"&gt;<br />
&lt;match url="^api/v2/user/transactions/mggame" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=HappistarRecord_mg" &nbsp; /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 59j"&gt;<br />
&lt;match url="^api/v2/user/transactions/nyxgame" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=HappistarRecord_nyx" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 60j"&gt;<br />
&lt;match url="^api/v2/user/transactions/scord" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_scordHistory" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 61j"&gt;<br />
&lt;match url="^api/v2/user/transactions/bonus" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_bonusHistory" &nbsp; /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 62j"&gt;<br />
&lt;match url="^api/v2/mobile/payment/withdrawal" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Moneyout_MobileNeteller" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 63j"&gt;<br />
&lt;match url="^api/v2/payment/withdrawal/methods" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Public_wmethods" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 64j"&gt;<br />
&lt;match url="^api/v2/payment/withdrawal" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Moneyout_DesktopNeteller" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 65j"&gt;<br />
&lt;match url="^api/v2/user/contact" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_contact" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 66j"&gt;<br />
&lt;match url="^api/v2/user/paymentcontracts" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Bank_happistarBank" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 67j"&gt;<br />
&lt;match url="^api/v2/mobile/custom/lostPassword" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=RecoveryPw_MobileApplyRecovery" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 68j"&gt;<br />
&lt;match url="^api/v2/custom/lostPassword" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=RecoveryPw_MobileApplyRecovery" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 69j"&gt;<br />
&lt;match url="^jp" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Language_HappiLang_lang_jp" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 70j"&gt;<br />
&lt;match url="^en" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Language_HappiLang_lang_en" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 71j"&gt;<br />
&lt;match url="^api/v2/mobile/setBonusStatus" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Index_setBonusStatus" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 72j"&gt;<br />
&lt;match url="^api/v2/mobile/levelupgrade" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Score_changeLevel" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 73j"&gt;<br />
&lt;match url="^api/v2/mobile/scoreexchange" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/m.php?s=Score_changeWallet" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 74j"&gt;<br />
&lt;match url="/authenticate.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_authenticate.html" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 75j"&gt;<br />
&lt;match url="/balance.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_balance.html" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 76j"&gt;<br />
&lt;match url="/bet.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_bet.html" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 77j"&gt;<br />
&lt;match url="/result.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_result.html" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 78j"&gt;<br />
&lt;match url="/bonusWin.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_bonusWin.html" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 79j"&gt;<br />
&lt;match url="/endRound.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_endRound.html" appendQueryString="false" /&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 80j"&gt;<br />
&lt;match url="/refund.html" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/user.php?s=/PragmaticPlay_refund.html" &nbsp;appendQueryString="false"/&gt;<br />
&lt;/rule&gt;<br />
<br />
&lt;rule name="rule 1j" stopProcessing="true"&gt;<br />
&lt;match url="^index.php$" &nbsp;/&gt;<br />
&lt;action type="Rewrite" url="/index.php?s=Index_indexStar" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
<br />
&lt;rule name="rule 81j"&gt;<br />
&lt;match url="^admin.php" &nbsp;/&gt;<br />
&lt;action type="Redirect" url="/index.php" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 82j"&gt;<br />
&lt;match url="^agent.php" &nbsp;/&gt;<br />
&lt;action type="Redirect" url="/index.php" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&lt;rule name="rule 83j"&gt;<br />
&lt;match url="^user.php" &nbsp;/&gt;<br />
&lt;action type="Redirect" url="/index.php" &nbsp;/&gt;<br />
&lt;/rule&gt;<br />
&nbsp; &nbsp; &nbsp; &lt;/rules&gt; &nbsp;<br />
&nbsp; &nbsp; &lt;/rewrite&gt; &nbsp;<br />
&nbsp;<br />
&nbsp; &lt;/system.webServer&gt; &nbsp;<br />
<br />
&nbsp; &nbsp;&nbsp;<br />
&lt;/configuration&gt; &nbsp;<br />
<br />
<br />