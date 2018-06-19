---
title: 如何在 Visual Studio 中設定部署屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2c6752e-c50d-4dd0-ac07-bf36ca10559c
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f448ec0569d64a3b3a14738bf08e68e083b80f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972988"
---
# <a name="how-to-set-deployment-properties-in-visual-studio"></a>如何在 Visual Studio 中設定部署屬性
在您可以從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署方案到 BizTalk 應用程式之前，您必須先設定專案屬性。 如果 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的方案包含多個專案，您必須個別為每一個專案設定屬性。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須使用具有本機檔案系統之讀取/寫入權限的帳戶登入。 本機電腦上的「系統管理員」帳戶具有這項權限。  
  
### <a name="to-enable-project-deployment-in-configuration-manager"></a>若要在組態管理員中啟用專案部署  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]按一下**建置**主功能表上，然後按一下**Configuration Manager**。  
  
2.  請檢查**部署**選項需要從開啟的方案部署的每個專案。  
  
### <a name="to-configure-project-properties"></a>若要設定專案屬性  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中以滑鼠右鍵按一下的專案，您要設定屬性，然後再按一下**屬性**。  
  
2.  按一下**部署**專案設計工具中的索引標籤。  
  
3.  下表中所述，設定專案屬性，然後按一下**確定**。  
  
4.  針對方案中的每個專案，重複步驟 1、2 和 3。  
  
    |屬性|值|說明|  
    |--------------|-----------|-----------------|  
    |Application Name|\<名稱\>|要部署此專案內組件的 BizTalk 應用程式名稱。 如果應用程式已經存在，組件便會在您部署專案時加入至其中。 如果應用程式不存在，則會建立該應用程式。 如果這個欄位是空白的，組件將會部署到目前群組中的預設 BizTalk 應用程式。 名稱如果包含空格，則必須括在雙引號 (") 中。|  
    |組態資料庫|\<BizTalk 管理資料庫名稱\>|群組的 BizTalk 管理資料庫名稱，依預設為 BizTalkMgmtDb。|  
    |Server|\<伺服器名稱\>|在本機電腦上，裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱。 在單一電腦安裝中，這通常是本機電腦的名稱。 **注意：** 如果您將這個 BizTalk 專案移至不同的電腦時，您可能必須修改以反映新的電腦名稱，您將能夠部署組件之前 [伺服器] 屬性。|  
    |重新部署|True 或 False|將此項設定為 True (預設)，可讓您不變更版本號碼而重新部署 BizTalk 組件。|  
    |安裝到全域組件快取|True 或 False|設定為 True (預設值) 會在您安裝應用程式時，將組件安裝到本機電腦上的全域組件快取 (GAC) 中。 只有當您打算在這項安裝中使用其他工具 (如 gacutil) 時，才能設定為 False。|  
    |重新啟動主控件執行個體|True 或 False|將此項設定為 True，可在重新部署組件時，自動重新啟動執行於本機電腦上的所有主控件執行個體。 如果設定為 False (預設)，您必須在重新部署組件時，手動重新啟動主控件執行個體。 **注意：** 如果您重新部署組件從方案層級時，主控件執行個體將會重新啟動一次每個專案，這個選項設為 True。 這樣可能會產生多次的重新啟動。 如果您打算從方案層級重新部署，您可能會想要只在方案中的一個專案上將此屬性設為 True，以免主控件執行個體重新啟動多次。 這應該在方案中最後一個將要重新部署的專案上設定。 此外，如果當您執行重新部署時，主控件執行個體停止了，它將不會啟動。|  
    |啟用單元測試|True 或 False|指定是否要對專案啟用單元測試。|  
  
## <a name="see-also"></a>請參閱  
 [從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)