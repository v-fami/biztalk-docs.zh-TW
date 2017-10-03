---
title: "AddResource 命令： 憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e915043-6634-4644-8d69-376d762c7cec
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fc2f1ca82dcd7a91f3572a4db96e9fc75f62839
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-certificate"></a>AddResource 命令：憑證
若要將安全性憑證加入至 BizTalk 應用程式，您使用**AddResource**命令，並指定**system.biztalk: certificate**型別參數。 為使這個命令能夠運作，憑證必須位於本機電腦上的「其他人」憑證存放區。  
  
 執行此命令會將憑證新增至 BizTalk 管理資料庫。 憑證也會顯示於 BizTalk Server 管理主控台，列在加入該憑證的應用程式的 [資源] 資料夾中。 此外，憑證時也將列出您使用[ListApp 命令](../core/listapp-command.md)。  
  
 當您安裝應用程式時，憑證隨即匯入到本機電腦上的「其他人」憑證存放區。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:Certificate** [**/Overwrite**] **/Thumbprint:"***值***"** [**/Server:***值*] [**/Database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或**/A**，請參閱 < 備註 >)|否|加入憑證的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 輸入**(或**/Ty**，請參閱 < 備註 >)|是|**System.biztalk: certificate** （此值不區分大小寫）。|  
|**/ 覆寫**(或**/O**，請參閱 < 備註 >)|否|此選項指定更新現有的憑證。 若未指定此選項，且應用程式中現有的憑證其 [指紋] 屬性與所加入的憑證相同，加入作業將會失敗。 若要查看 [指紋] 屬性，請在 [憑證] 嵌入式管理單元中按兩下憑證，然後按一下 [詳細資料] 索引標籤。如需詳細資訊，請參閱 [憑證] 嵌入式管理單元說明文件中的＜檢視憑證資訊＞。|  
|**/ 指紋**(或**t**，請參閱 < 備註 >)|是|憑證指紋屬性 (*指紋*是資料的摘要)。 此值必須括在雙引號 (") 中。|  
|**/ 伺服器**(或**/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或**/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication/類型： system.biztalk: certificate 覆寫 /Thumbprint:"04 a2 8e 32 24 f9 36 b9 42 81 12 71 3a d2 ef db c7 9 c 83 dc"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將憑證新增至應用程式](../core/how-to-add-a-certificate-to-an-application.md)