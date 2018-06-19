---
title: 如何新增前置或後置處理指令碼至應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], adding scripts
- managing [scripts], applications
- applications, scripts
- managing [scripts], adding
- scripts, adding to applications
- scripts
ms.assetid: 729cb236-b9cf-468a-8b98-a24d86e60d3c
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d0646bc9e896e7b4e4d9264efba7c9bb5f0eb66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248446"
---
# <a name="how-to-add-a-pre--or-post-processing-script-to-an-application"></a>如何新增前置或後置處理指令碼至應用程式
本主題說明如何使用 BizTalk Server 管理主控台或命令列，將前置或後置處理指令碼新增至應用程式。 當您將指令碼加入至應用程式時，指令碼會包含在應用程式 .msi 檔案中，並且會在匯入、安裝或解除安裝應用程式時執行。  
  
 加入指令碼時，您必須指定它是前置處理指令碼 (會在應用程式匯入或安裝啟動之前執行)，還是後置處理指令碼 (會在應用程式匯入或安裝完成之後執行)。 前置和後置處理指令碼也在解除安裝，可在安裝時執行的相反順序執行： 前置處理指令碼執行之後解除安裝和解除安裝之前執行的後置處理指令碼。  
  
 您也可以從應用程式移除指令碼。 如需指示，請參閱[如何移除前置或後置處理指令碼，從應用程式](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-script-to-an-application"></a>若要新增指令碼至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  依序展開 BizTalk 群組和 [應用程式]，然後以滑鼠右鍵按一下要新增指令碼之應用程式的資料夾。  
  
3.  指向**新增**，執行下列其中一項：  
  
    -   按一下**前置處理指令碼**如果您想要應用程式匯入之前執行的指令碼，或開始安裝或解除安裝之後。  
  
    -   按一下**後置處理指令碼**如果您想要執行應用程式匯入或安裝後，或在解除安裝之前的指令碼。  
  
4.  按一下**新增**並瀏覽至要加入的指令碼檔案。  
  
5.  選取的指令碼檔案，然後按一下**開啟**。  
  
6.  如果您想要覆寫已經在應用程式中，選取的指令碼檔案**覆寫所有**核取方塊。 指令碼檔案必須與新增檔案同名，才會被覆寫。 否則，加入新指令碼時，應用程式中的現有指令碼會維持不變。  
  
7.  按一下**檔案類型**下拉式清單，然後按一下該檔案類型 – 請**system.biztalk: preprocessingscript**或**system.biztalk: postprocessingscript**。  
  
8.  必要時，在**目的地位置**類型要指令碼的路徑檔案安裝應用程式時，要複製，然後按一下**確定**。 預設路徑會將指令碼安裝到應用程式安裝資料夾 (%BTAD_InstallDir%)。  
  
> [!NOTE]
>  如果您沒有提供這個路徑，在安裝時，就不會將指令碼複製到本機檔案系統。 如果這個指令碼應該會在應用程式解除安裝時執行，請務必提供這個路徑；否則，指令碼不會出現在本機檔案系統中，並且無法在解除安裝期間執行。  
  
 指令碼隨即加入至應用程式，而且會顯示在應用程式的 [Resources] 資料夾中。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:PreProcessingScript**&#124;**System.biztalk: postprocessingscript** [**/覆寫**] **/source:***值*[**/Destination:** *值*] [**/Server:***值*] [**/database:***值*] [**/Property:Args ="***引數清單***"**]  
  
     範例：  
  
     **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:PreProcessingScript / 覆寫 /Source:"C:\Source Scripts\MyScript.vbs"/Destination:"C:\New Scripts\MyScript.vbs"/Server:MyDatabaseServer /Database:BizTalkMgmtDb/Property:Args ="引數 1 引數 2"**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入指令碼之 BizTalk 應用程式的名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: preprocessingscript**或**system.biztalk: postprocessingscript**，端視要加入的指令碼類型。 使用**system.biztalk: preprocessingscript**如果您想要執行應用程式匯入或安裝前或解除安裝後指令碼。 使用**system.biztalk: postprocessingscript**如果您想要執行應用程式匯入或安裝後，或在解除安裝之前的指令碼。|  
    |**/ 覆寫**|更新現有的指令碼。 如果未指定此選項，而且應用程式中現有的指令碼檔案與所加入的指令碼檔案同名，加入作業將會失敗。|  
    |**/ 來源**|指令碼檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 目的地**|從 MSI 檔案安裝應用程式時，指令碼檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
    |**/Property:Args =**|零或多個引數。 在此提供的引數會在叫用指令碼時傳入指令碼。|  
  
## <a name="see-also"></a>另請參閱  
 [管理前置或後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md)   
 [AddResource 命令： 前置處理指令碼](../core/addresource-command-preprocessing-script.md)   
 [AddResource 命令： 後置處理指令碼](../core/addresource-command-postprocessing-script.md)