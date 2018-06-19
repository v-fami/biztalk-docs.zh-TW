---
title: 如何移除其他檔案和設定 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], deleting settings
- managing [applications], deleting files
- undeploying, settings
- applications, undeploying
- undeploying, files
ms.assetid: b947831a-c988-435c-92ec-45f3fd6967de
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9ad98e0f0fc1e65281a1d8195be4f4a708d004f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255062"
---
# <a name="how-to-remove-other-files-and-settings-for-a-biztalk-application"></a>如何移除 BizTalk 應用程式的其他檔案和設定
本主題描述如何移除檔案和設定可能不會移除當您解除安裝應用程式的 BizTalk 應用程式 (如所述[如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md))。 例如，除非應用程式包含可以在解除安裝時移除憑證、COM 和 COM+ 登錄項目以及 COM 檔案的後置處理指令碼，否則這些項目都不會移除。  
  
> [!CAUTION]
>  然後再移除任何共用的項目，請確定沒有其他應用程式使用它們，或應用程式將無法正確運作。  
  
> [!NOTE]
>  建議您使用後置處理指令碼自動執行這項移除作業。 如需詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
-   **刪除憑證。** 有兩種方法可以從憑證存放區刪除憑證：使用憑證管理員 (certmgr.exe) 命令列工具或憑證嵌入式管理單元。 Certmgr.exe 會隨.NET SDK，也就是其中一個的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝的必要條件。 您可以手動執行 certmgr.exe，也可以從後置處理指令碼執行。 如需使用 certmgr.exe 的詳細資訊，請參閱[憑證管理員工具 (certmgr.exe)](http://go.microsoft.com/fwlink/?LinkId=56198)羰 Microsoft 寍鯚。  
  
     憑證嵌入式管理單元包含在 Windows Server 2008 和 Windows Vista 中。 若要刪除憑證，請依照作業系統說明中「啟動憑證嵌入式管理單元」所述，開啟嵌入式管理單元，然後再依憑證說明中「刪除憑證」所述，刪除憑證。  
  
-   **從 Windows 登錄中移除組件。** 若要從 Windows 登錄移除 .NET 和 BizTalk 組件，請使用 .NET SDK 中隨附的 regsvcs 或 regasm，.NET SDK 是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的其中一項必要安裝條件。 如需參考資訊，請參閱[.NET 服務安裝工具 (Regsvcs.exe)](http://go.microsoft.com/fwlink/?LinkId=56199)和[組件註冊工具 (Regasm.exe)](http://go.microsoft.com/fwlink/?LinkId=56200)羰 Microsoft 寍鯚。  
  
-   **從 Windows 登錄中移除 COM 元件。** 若要從 Windows 登錄中移除 COM 元件，請使用 regsvr32。 如需參考資訊，請參閱作業系統「說明」中的「Regsvr32」。 此工具包含在 Windows Server 2008 和 Windows Vista Professional 中。  
  
-   **解除安裝組件從全域組件快取 (GAC)。** 組件不會自動從 GAC 中解除安裝。 您可以使用手動方式或使用指令碼從 GAC 中解除安裝組件。 如需詳細資訊，請參閱[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)。  
  
## <a name="prerequisites"></a>必要條件  
 若要移除本主題中所描述的檔案和設定，您必須依據想要移除的項目，使用具有 Windows 登錄、GAC 或憑證存放區之寫入權限的身分登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)   
 [如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)