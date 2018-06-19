---
title: 重複使用 SAP 配接器繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding file, definition
- adapter bindings, reusing
ms.assetid: 5748c22f-20a2-4eb9-ad45-a1bef7290802
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df4c878f8eb6a5e1fd52dfe749b10d1d89716679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217694"
---
# <a name="reuse-sap-adapter-bindings"></a>重複使用 SAP 配接器繫結
繫結之間建立對應的邏輯端點 （例如協調流程連接埠或角色連結） 與實體端點 (例如傳送和接收埠)。 這讓通訊能在不同的 BizTalk 商務方案元件之間進行。 您可以使用 [BizTalk Server 管理主控台] 建立繫結。  
  
## <a name="what-is-a-binding-file"></a>什麼是繫結檔案？  
 繫結檔案是 XML 檔案，其中包含每個 BizTalk 協調流程範圍中的 BizTalk 組件、 應用程式或群組的繫結資訊。 描述繫結檔案：  
  
-   每個協調流程繫結至主機
  
-   主控件的信任層級
  
-   每個設定傳送埠、 接收埠、 接收位置，以及已設定合作對象
  
 您可以產生繫結檔案，然後將它們包含的繫結套用至組件、 應用程式或群組。 這可避免必須手動設定在不同的部署環境中的 繫結，並可加速應用程式部署。  
  
繫結檔案不會自動產生 BizTalk 組件、 應用程式或群組。 不過，您可以產生繫結檔案匯出繫結。 您可以再將繫結檔案匯入的應用程式或群組。  
  
如需有關繫結和繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../../core/binding-files-and-application-deployment.md)。
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。
 
## <a name="export-bindings"></a>匯出繫結
本章節描述如何匯出成 XML 檔案的 BizTalk 應用程式的繫結。 您接著可以從 XML 檔案的繫結匯入到另一個 BizTalk 應用程式。 匯入繫結會覆寫任何現有的繫結的應用程式中相同的名稱。 您也可以將繫結加入應用程式中，這樣並不會覆寫現有的繫結。 加入的繫結會在您匯入該應用程式之後才生效。  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  以滑鼠右鍵按一下您想要匯出其繫的結選取的應用程式**匯出**，然後選取**繫結**。  
  
4.  在**匯出繫結**頁面上，於**匯出至檔案**，輸入要匯出繫結至 XML 檔案的絕對路徑。  
  
     例如，輸入`C:\Bindings\Application1Bindings.Binding1.xml`  
  
5.  確認**從目前的應用程式匯出所有繫結**已選取。  
  
6.  若要匯出群組的所有合作對象資訊，請選取**匯出全域合作對象資訊**核取方塊。  
  
7.  選取 [確定]。 繫結會匯出到 XML 檔案中您所指定的位置。  

## <a name="import-bindings"></a>匯入繫結
匯入繫結使用 BizTalk Server 管理主控台。
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  以滑鼠右鍵按一下想要匯入繫結，請選取的應用程式**匯入**，然後選取**繫結**。  
  
4.  選取繫結檔案，然後選取**開啟**。  
  
繫結檔案中的成品會寫入此應用程式， 這些成品會顯示在應用程式的適當資料夾中。 例如，傳送埠會一併匯入繫結顯示底下的**傳送埠**資料夾。  

## <a name="passwords-are-removed"></a>密碼會移除  
基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您的 [傳輸屬性] 對話方塊中設定密碼[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理主控台的 傳送埠或接收位置。 

指定使用者名稱和密碼的相關資訊，請參閱[設定登入 SAP 系統的認證](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md)。

## <a name="see-also"></a>另請參閱
[若要建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)