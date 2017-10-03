---
title: "AddResource 命令： BizTalk 繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c732d3-82c8-4615-b68f-ed29b54ebbf3
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e19e1961293002e8b4169a6fee55708cf3217d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command-biztalk-binding"></a>AddResource 命令：BizTalk 繫結
若要將繫結檔案加入至 BizTalk 應用程式，您使用**AddResource**命令，並指定**system.biztalk: biztalkbinding**如**類型**參數。 加入繫結檔案後，您就能為該檔案指定部署環境。 當您日後匯入應用程式時，可以選取此部署環境以便套用繫結。 每個 BizTalk 應用程式可加入任意數目的繫結檔案，以針對不同的部署環境自訂個別檔案。 若要加入多個繫結檔案，請逐次執行此命令一一加入各檔案。  
  
 中所述，您可以加入繫結檔案匯出的組件、 應用程式或群組， [ExportBindings 命令](../core/exportbindings-command.md)，然後使用 AddResource 命令將繫結檔案新增至應用程式。  
  
 執行此命令會將繫結檔案新增至 BizTalk 管理資料庫，而檔案也會顯示在應用程式的 [資源] 資料夾中。 此外，檔案時也將列出您使用[ListApp 命令](../core/listapp-command.md)。 與匯入繫結檔案不同，加入繫結檔案不會立即改變現有的繫結。 當應用程式匯入到其他 BizTalk 群組時才會套用繫結。  
  
 加入繫結檔案時，您可以使用選擇性參數 "TargetEnvironment" /Property 指定其部署環境。 此參數值可為任意字串，代表這個檔案中的繫結將要套用於哪一種部署環境，例如「測試」或「生產」。 如果您未指定 /Property 參數的值的值**\<預設 >**自動指定，且會套用此繫結檔案匯入應用程式每次。  
  
 當您以這種方式明確加入一或多個繫結檔案後，匯入含有這些檔案的應用程式時，即可藉由指定 /Property 參數的值來選擇所要套用的繫結檔案。 應用程式匯入期間將套用繫結。  
  
 由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。 也就是說，同名的繫結當中最後套用的繫結將會生效。 使用多個繫結檔案時務必留意這種情況。 如果這些檔案包含重複的項目，最後套用的繫結則為實際生效的項目。 當您匯入應用程式時，將依下列順序套用繫結：  
  
1.  並非透過繫結檔案明確加入至應用程式，而是使用者明確選定欲匯出至應用程式 .msi 檔案的應用程式繫結 (由 BizTalk Server 所產生)。  
  
2.  已明確加入，但未指定目標部署環境的繫結檔案。 套用此集合中的繫結時，並無特定順序。  
  
3.  已明確加入，且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。 套用此集合中的繫結時，並無特定順序。  
  
 如需詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 如需使用繫結檔案的背景資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:"***值***"**] **/Type:System.BizTalk:BizTalkBinding/Property:TargetEnvironment ="***值***"** [**/覆寫**] **/source:***值*[**/Server:***值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或**/A**，請參閱 < 備註 >)|否|加入繫結檔案的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。|  
|**/ 輸入**(或**/T**，請參閱 < 備註 >)|是|**System.biztalk: biztalkbinding** （此值不區分大小寫）。|  
|**/ 來源**(或**/So**，請參閱 < 備註 >)|是|繫結檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/Property:TargetEnvironment =** (或**/P:TargetEnvironment =**，請參閱 < 備註 >)|否|用於指定目標部署環境的字串。 您可以使用任意字串，例如「實際執行」。 範例： **/Property:TargetEnvironment = 「 生產 」**<br /><br /> 如果未指定值為**\<預設 >**自動套用。 此值區分大小寫。 如果參數值包含空格，您必須將它括在雙引號 (") 中。 環境值的長度上限為 128 個字元。|  
|**/ 覆寫**(或**/Ov**，請參閱 < 備註 >)|否|此選項指定更新現有的繫結檔案。 若未指定此選項，且應用程式中現有的繫結檔案與所加入的繫結檔案同名，AddResource 作業將會失敗。|  
|**/ 伺服器**(或**/Se**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或**/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:BizTalkBinding /Property:TargetEnvironment = 測試 /Source:"C:\Binding Files\MyBinding.xml"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 屬性名稱區分大小寫。 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)