---
title: FTP 配接器組態屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, adapters
- FTP adapters, properties
- FTP adapters, code sample
- FTP adapters, send ports
- FTP adapters, receive locations
- send ports, adapters
ms.assetid: 88a2084e-cb26-4136-9077-8b9463062ccc
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29124c17603abbc9b38a078238d13cdfb1c992e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975268"
---
# <a name="ftp-adapter-configuration-properties"></a>FTP 配接器組態屬性
下表列出可為 FTP 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|指定接收位置所監控之位置的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|serverAddress|VT_BSTR|指定 FTP 伺服器的伺服器名稱或 IP 位址。|無|無|  
|serverPort|VT_BSTR|指定要用來與目標 FTP 伺服器通訊的 TCP 連接埠。|無|無|  
|userName|VT_BSTR|指定用來存取 FTP 伺服器的使用者名稱。|無|無|  
|密碼|VT_BSTR|指定用來存取 FTP 伺服器的密碼。|當匯出繫結檔案時，一定會遮罩這個值。 將繫結檔案匯入到目標 BizTalk Server 組態之前，必須在此屬性中手動填入密碼。|無|  
|fileMask|VT_BSTR|指定傳輸檔案時要使用的檔案遮罩篩選。|無|無|  
|targetFolder|VT_BSTR|指定 FTP 伺服器上的輪詢位置。|無|無|  
|commandLogFilename|VT_BSTR|指定要用來儲存記錄檔複本的位置。|無|您可以使用此檔案來診斷透過 FTP 配接器傳送或接收檔案時所發生的錯誤情況。|  
|representationType|VT_BSTR|選取 FTP 配接器接收資料的方式。|有效值為：<br /><br /> -二進位<br />ASCII|預設值為 Binary。|  
|spoolingFolder|VT_BSTR|指定 FTP 伺服器上的暫存資料夾位置。 您會使用此資料夾以保證能夠從傳輸失敗回復。|無|無|  
|receiveDataTimeOut|VT_BSTR|指定接收呼叫中止前時間 (以毫秒為單位)。 這可用來防止伺服器過慢而導致接收位置沒有反應。|無|預設值是 90000。|  
|maximumBatchSize|VT_BSTR|指定每個 BizTalk Server 批次的最大位元組數。|無|無|  
|maximumNumberOfFiles|VT_BSTR|指定每個 BizTalk Server 批次的檔案數目上限。|無|無|  
|passiveMode|VT_BSTR|指定配接器與 FTP 伺服器之間的連接模式。|有效值為：<br /><br /> -被動<br />-使用中|預設值為 Active。|  
|useNLST|VT_BSTR|將這個屬性指定為 Yes，會只擷取檔案名稱，而不擷取預設的系統定義檔案清單。|有效值為：<br /><br /> -[是]<br />-無|預設值為 No。|  
|beforeGet|VT_BSTR|指定檔案 GET 前要執行的 FTP 命令。|使用分號 （;） 來分隔命令**附註：** 檔案 GET 前不支援 QUIT 命令。|無|  
|afterGet|VT_BSTR|指定檔案 GET 後要執行的 FTP 命令。|使用分號 (;) 來分隔命令。|無|  
|firewallType|VT_BSTR|指定部署的防火牆類型。|有效值為：<br /><br /> -無<br />-Socks 4<br />Socks 5|預設值為 [無]。|  
|firewallAddress|VT_BSTR|指定防火牆的位址 (DNS 名稱或 IP 位址)。|無|無|  
|firewallPort|VT_BSTR|指定防火牆的連接埠。|有效值從 1 到 65535 之間。|預設值為 21。|  
|firewallUserName|VT_BSTR|指定防火牆的使用者名稱。|無|無|  
|firewallPassword|VT_BSTR|指定防火牆的密碼。|無|無|  
|pollingUnitOfMeasure|VT_BSTR|指定 pollingInterval 屬性的單位類型。|有效值為：<br /><br /> 秒<br />-分鐘<br />-小時<br />天|預設值為 [秒]。|  
|pollingInterval|VT_BSTR|指定輪詢此位置的間隔值。|無|若要連續輪詢，請將此值設為零 0。<br /><br /> 預設值為 60。|  
|redownloadInterval|VT_BSTR|指定 FTP 配接器會再次下載檔案的間隔 (以秒數為單位)。|只有在 deleteAfterDownload 和 enableTimeComparison 屬性都設為 [否] 時 ， 才能套用這個屬性 。|值為 -1 表示配接器不會再次下載檔案。<br /><br /> 預設值為-1。|  
|ssoAffiliateApplication|VT_BSTR|指定 單一登入 (SSO) 分支機構應用程式 。|無|無|  
|errorThreshold|VT_BSTR|指定在停用位置之前，容許 BizTalk Server 發生的錯誤數目。|無|預設值是 10。|  
|maxFileSize|VT_BSTR|指定可下載的檔案大小上限，以 MB 為單位。|無|0 的值表示檔案大小無限制。<br /><br /> 預設值為 100。|  
|useSsl|VT_BSTR|如果 FTP 配接器必須使用 SSL 來與 FTPS 伺服器通訊，請將這個屬性指定為 Yes。|有效值為：<br /><br /> -[是]<br />-無|預設值為 No。|  
|useDataProtection|VT_BSTR|如果 FTP 配接器必須使用 SSL 加密來與 FTPS 伺服器往返傳送檔案，請將這個屬性指定為 Yes。|如果將 useSsl 屬性設定為 Yes，這個屬性就有效。<br /><br /> 有效值為：<br /><br /> -[是]<br />-無|預設值為 Yes。|  
|ftpsConnMode|VT_BSTR|指定對 FTPS 伺服器的 SSL 連線模式。|有效值為：<br /><br /> 明確<br />隱含|預設值為 [明確]。|  
|clientCertificateHash|VT_BSTR|指定必須在 SSL 交涉中使用之用戶端憑證的 SHA1 雜湊。|無|系統會根據此雜湊，從用於執行 BizTalk 主控件執行個體之使用者帳戶的個人存放區挑選用戶端憑證。|  
|deleteAfterDownload|VT_BSTR|如果配接器必須在下載完成後從 FTP 伺服器刪除檔案，請將這個屬性指定為 Yes。|有效值為：<br /><br /> -[是]<br />-無|預設值為 Yes。|  
|enableTimeComparison|VT_BSTR|如果配接器必須在檔案的時間戳記有所變更時再次下載檔案，請將這個屬性指定為 Yes。|只有在 deleteAfterDownload 設為 No 時，這個屬性才有效。<br /><br /> 目標 FTP 伺服器必須支援這項功能的 MDTM 命令。<br /><br /> 有效值為：<br /><br /> -[是]<br />-無|預設值為 No。|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>ftp://localhost:21/in/*.xml</uri><serverAddress>localhost</serverAddress><serverPort>21</serverPort><userName>domain\testuser</userName><password>******</password><fileMask>*.xml</fileMask><targetFolder>in</targetFolder><commandLogFilename>c:\temp\realftplog.txt</commandLogFilename><representationType>binary</representationType><maximumBatchSize>0</maximumBatchSize><maximumNumberOfFiles>0</maximumNumberOfFiles><passiveMode>False</passiveMode><firewallType>NoFirewall</firewallType><firewallPort>21</firewallPort><pollingUnitOfMeasure>Seconds</pollingUnitOfMeasure><pollingInterval>5</pollingInterval><errorThreshold>10</errorThreshold><maxFileSize>5000</maxFileSize><useSsl>False</useSsl><useDataProtection>True</useDataProtection><ftpsConnMode>Explicit</ftpsConnMode><clientCertificateHash>‎bc 32 2c a9 22 75 6a 3f e4 f7 a9 b1 b3 3a 24 20 23 53 68 49</clientCertificateHash><deleteAfterDownload>True</deleteAfterDownload><enableTimeComparison>False</enableTimeComparison></Config></AdapterConfig></CustomProps>  
```  
  
 下表列出可為 FTP 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|指定資料傳送之目標位置的完整路徑。|傳送埠或接收位置的 URI 不能超過 256 個字元。|無|  
|serverAddress|VT_BSTR|指定防火牆的位址，可指定 DNS 名稱或 IP 位址。|無|無|  
|serverPort|VT_BSTR|指定 FTP 伺服器的連接埠位址。|無|預設值為 21。|  
|userName|VT_BSTR|指定要用來登入 FTP 伺服器的使用者名稱。|無|無|  
|密碼|VT_BSTR|指定要用來登入 FTP 伺服器的密碼。|當匯出繫結檔案時，一定會遮罩這個值。 將繫結檔案匯入到目標 BizTalk Server 組態之前，必須在此屬性中手動填入密碼。|無|  
|accountName|VT_BSTR|指定 FTP 伺服器的帳戶名稱。|選擇性|無|  
|targetFolder|VT_BSTR|指定在 FTP 伺服器上移動檔案的位置。|無|無|  
|targetFileName|VT_BSTR|為檔案指定別名。 保留預設名稱可確保每一個傳送的訊息都擁有唯一的訊息名稱。|無|預設值為 %MessageID%.xml。|  
|commandLogFilename|VT_BSTR|指定要用來儲存記錄檔複本的位置。 使用記錄檔來診斷透過 FTP 伺服器傳送或接收檔案時所發生的錯誤情況。|無|無|  
|representationType|VT_BSTR|選取 FTP 傳送資料的方式 (二進位或 ASCII)。|有效值為：<br /><br /> -二進位<br />ASCII|預設值為 binary。|  
|beforePut|VT_BSTR|指定檔案 PUT 前要執行的 FTP 命令，例如，要在 FTP 伺服器上變更預設值的命令。|使用分號 (;) 來分隔命令。 **注意：** 檔案 PUT 前不支援 QUIT 命令。|不需要開啟命令。|  
|afterPut|VT_BSTR|指定檔案 PUT 後要執行的 FTP 命令。|使用分號 (;) 來分隔命令。|無|  
|allocateStorage|VT_BSTR|指定是否配置儲存空間給舊版主控件系統。|有效值為：<br /><br /> -[是]<br />-無|預設值為 No。|  
|spoolingFolder|VT_BSTR|指定 FTP 伺服器上的暫存資料夾位置。 如果傳輸模式為二進位，則您會使用此資料夾以保證能夠從傳輸失敗回復。 如果傳輸模式為 ASCII，配接器就會重新開始上傳。|無|無|  
|connectionLimit|VT_BSTR|指定伺服器最多可以開啟的並行 FTP 連線數目。|無|值為 0 時表示沒有限制。|  
|passiveMode|VT_BSTR|指定是要使用被動模式還是主動模式。|有效值為：<br /><br /> -True （被動模式）<br />False （主動模式）|預設值為 False (主動模式)。|  
|firewallType|VT_BSTR|選取部署之防火牆的類型。|有效值為：<br /><br /> -Socks 4<br />Socks 5<br />-無|預設值為 [無]。|  
|firewallAddress|VT_BSTR|指定防火牆的位址，可指定 DNS 名稱或 IP 位址。|無|無|  
|firewallPort|VT_BSTR|指定防火牆的連接埠。|有效值從 1 到 65535 之間。|預設值為 21。|  
|firewallUserName|VT_BSTR|指定防火牆的使用者名稱。|無|無|  
|firewallPassword|VT_BSTR|指定防火牆的密碼。|當匯出繫結檔案時，一定會遮罩這個值。 將繫結檔案匯入到目標 BizTalk Server 組態之前，必須在此屬性中手動填入密碼。|無|  
|ssoAffiliateApplication|VT_BSTR|指定 單一登入 (SSO) 分支機構應用程式 。|無|無|  
|useSsl|VT_BSTR|如果 FTP 配接器必須使用 SSL 來與 FTPS 伺服器通訊，請將這個屬性指定為 Yes。|有效值為：<br /><br /> -[是]<br />-無|預設值為 No。|  
|useDataProtection|VT_BSTR|如果 FTP 配接器必須使用 SSL 加密來與 FTPS 伺服器往返傳送檔案，請將這個屬性指定為 Yes。|如果 useSsL 設定為 Yes，這個屬性就有效。<br /><br /> 有效值為：<br /><br /> -[是]<br />-無|預設值為 Yes。|  
|ftpsConnMode|VT_BSTR|指定對 FTPS 伺服器的 SSL 連線模式。|有效值為：<br /><br /> 明確<br />隱含|預設值為 [明確]。|  
|clientCertificateHash|VT_BSTR|在 SSL 交涉中，指定必須使用用戶端憑證的 SHA1 雜湊。|無|系統會根據此雜湊，從用於執行 BizTalk 主控件執行個體之使用者帳戶的個人存放區挑選用戶端憑證。|  
  
 下列程式碼顯示您用來設定屬性的字串格式：  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><serverAddress>TestServer</serverAddress><serverPort>21</serverPort><userName>testuser</userName><password>******</password><accountName>testuser</accountName><targetFolder>output</targetFolder><targetFileName>%MessageID%.xml</targetFileName><commandLogFilename>c:\logfile\ftpsendlog.txt</commandLogFilename><representationType>binary</representationType><beforePut>CDW dir</beforePut><afterPut>CDUP </afterPut><allocateStorage>False</allocateStorage><spoolingFolder>tempfolder</spoolingFolder><connectionLimit>0</connectionLimit><passiveMode>False</passiveMode><firewallType>Socks4</firewallType><firewallAddress>TestServer</firewallAddress><firewallPort>21</firewallPort><firewallUserName>domain\testuser</firewallUserName><firewallPassword>******</firewallPassword><useSsl>False</useSsl><useDataProtection>True</useDataProtection><ftpsConnMode>Explicit</ftpsConnMode><clientCertificateHash>‎bc 32 2c a9 22 75 6a 3f e4 f7 a9 b1 b3 3a 24 20 23 53 68 49</clientCertificateHash><uri>ftp://TestServer:21/output/%MessageID%.xml</uri></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  指定時使用配接器架構建置配接器的 TransportTypeData 組態資料，所使用的所有名稱/值組必須都儲存成\<AdapterConfig\>項目。 因為\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料型別然後\<\>必須逸出字元資料中的。