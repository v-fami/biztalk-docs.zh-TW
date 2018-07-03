---
title: 如何將原則新增至應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [policies], adding to applications
- policies, applications
- applications, policies
- policies, adding to applications
ms.assetid: 93b3ce5e-8c63-4c64-9bdc-1747541ba9a8
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2fe3d2b217757d9d06b1954a5d950f4ea88bd91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004063"
---
# <a name="how-to-add-a-policy-to-an-application"></a>如何新增原則至應用程式
本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，將原則新增至 BizTalk 應用程式。 使用管理主控台時，您可以新增多個原則，一次。 新增原則至應用程式可以讓該原則提供給該應用程式以及參考它的其他任何應用程式使用。  
  
 當您新增原則至應用程式時，請牢記下列要點：  
  
-   您可以將原則新增至應用程式的原則必須存在於 BizTalk 群組，規則引擎資料庫，必須將它發行，如中所述之前[如何匯入原則](../core/how-to-import-a-policy.md)。  
  
    > [!NOTE]
    >  當您使用 [規則引擎部署精靈] 從「規則引擎」資料庫移除原則後，該原則依然會出現在管理主控台中，不過您將無法予以發佈。 如需有關 「 規則引擎部署精靈 」 的詳細資訊，請參閱[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。  
  
-   此原則不能已存在於 BizTalk 群組的另一個應用程式中。  
  
    > [!IMPORTANT]
    >  如果原則是由兩個或多個應用程式所共用，您應該建立個別的應用程式來容納此原則，然後建立參考，從使用此原則的應用程式參考到包含此原則的應用程式。 這是因為如果您停止了包含原則的應用程式，該原則就會自動解除部署，而且任何使用此原則的應用程式都將無法再使用它。 如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
-   原則也必須部署之後，才會生效並開始運作。 原則會自動部署應用程式啟動時，或您可以手動將它們部署中所述[如何部署或解除部署原則](../core/how-to-deploy-or-undeploy-a-policy.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-policy-to-an-application"></a>新增原則至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和 BizTalk 群組。  
  
3. 展開 應用程式中，展開您想要新增原則，並以滑鼠右鍵按一下應用的程式**原則**。  
  
4. 指向**新增**然後按一下**原則**。  
  
5. 選取每個原則和版本來新增，然後按一下核取方塊**確定**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Rules** [**覆寫**] **/Name:**<em>值</em>**/Version:**<em>值</em>[**/Server:**<em>值</em>] [**/Database:**<em>值</em>]  
  
   > [!NOTE]
   >  參數值會區分大小寫。 參數名稱不區分大小寫。 此外，當您使用這個命令新增原則至應用程式時，也會自動新增該原則所使用的任何詞彙。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
    範例  
  
    **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Rules / 覆寫 /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 應用程式名稱**|加入原則的 BizTalk 應用程式的名稱。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。 名稱如果包含空格，則必須括在雙引號 (") 中。|  
   |**/ 類型**|**System.biztalk: rules**|  
   |**/ 覆寫**|此選項指定更新現有的原則。 若未指定此選項，且應用程式中現有的原則與所加入的原則同名，AddResource 作業將會失敗。|  
   |**/ 名稱**|此原則的名稱。|  
   |**/ 版本**|原則的版本號碼。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。 如果您指定 Database 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果您指定 Server 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理原則](../core/managing-policies.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [AddResource 命令：原則](../core/addresource-command-policy.md)