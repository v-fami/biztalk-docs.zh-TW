---
title: 重複使用 Siebel 配接器中的配接器繫結 |Microsoft Docs
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
ms.assetid: 1dc17b7a-5397-43f4-b19e-9c50fb0e97ff
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3a85346b44a88b5776e9f586ddc56675f8ef9ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007039"
---
# <a name="reuse-adapter-bindings-in-the-siebel-adapter"></a>Siebel 配接器中的重複使用配接器繫結
繫結會在邏輯端點 (例如協調流程連接埠或角色連結) 與實體端點 (例如傳送和接收埠或合作對象) 之間建立對應。 這讓通訊能在不同的 BizTalk 商務方案元件之間進行。 您可以使用 [BizTalk Server 管理主控台] 建立繫結。  
  
## <a name="what-is-a-binding-file"></a>何謂繫結檔案？  
繫結檔案是 XML 檔案，其中包含 BizTalk 組件、 應用程式或群組的範圍中每個 BizTalk 協調流程的繫結資訊。 描述繫結檔案：  
  
- 每個協調流程繫結至主應用程式
  
- 主控件的信任層級
  
- 每個設定傳送埠、 接收埠、 接收位置，以及已設定的合作對象
  
  您可以產生繫結檔案，然後將它們包含的繫結套用至組件、 應用程式或群組。 這可避免必須以手動方式設定在不同的部署環境中的 繫結，並加快應用程式部署。  
  
  BizTalk 組件、 應用程式或群組不會自動產生繫結檔案。 不過，您可以產生繫結檔案匯出繫結。 您可以接著將繫結檔案匯入的應用程式或群組。  
  
  如需有關繫結和繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../../core/binding-files-and-application-deployment.md)。
 
  > [!NOTE]
  >  BizTalk 組件、 應用程式或群組不會自動產生繫結檔案。 但是，您可以產生繫結檔案匯出繫結。 您可以接著將繫結檔案匯入的應用程式或群組。  
  
## <a name="prerequisites"></a>必要條件  
登入第 i 個成員的帳戶[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。

 
## <a name="export-bindings"></a>匯出繫結
本節說明如何匯出到 XML 檔案的 BizTalk 應用程式的繫結。 您接著可以從 XML 檔案的繫結匯入至另一個 BizTalk 應用程式。 匯入繫結會覆寫任何現有的繫結的應用程式中相同的名稱。 您也可以將繫結加入應用程式中，這樣並不會覆寫現有的繫結。 加入的繫結會在您匯入該應用程式之後才生效。  
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 以滑鼠右鍵按一下 應用程式，選取您想要匯出其繫的結**匯出**，然後選取**繫結**。  
  
4. 在 **匯出繫結**頁面上，於**匯出至檔案**，輸入要匯出繫結至 XML 檔案的絕對路徑。  
  
    例如，輸入 `C:\Bindings\Application1Bindings.Binding1.xml`  
  
5. 確認**從目前的應用程式匯出所有繫結**已選取。  
  
6. 若要匯出群組的所有合作對象資訊，請選取**匯出全域合作對象資訊**核取方塊。  
  
7. 選取 [確定]。 繫結都會匯出至 XML 檔案中您所指定的位置。  

## <a name="import-bindings"></a>匯入繫結
匯入繫結使用 BizTalk Server 管理主控台。
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 以滑鼠右鍵按一下想要匯入繫結，請選取的應用程式**匯入**，然後選取**繫結**。  
  
4. 選取繫結檔案，然後選取**開啟**。  
  
繫結檔案中的成品會寫入此應用程式， 這些成品會顯示在應用程式的適當資料夾中。 例如，傳送埠匯入繫結顯示下一部分**傳送埠**資料夾。  

## <a name="passwords-are-removed"></a>密碼會移除  
基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您在的 [傳輸屬性] 對話方塊中設定密碼[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理主控台的 傳送埠或接收位置。 

指定使用者名稱和密碼的相關資訊，請參閱[設定登入認證，siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-sign-in-credentials-for-the-siebel.md)。

## <a name="see-also"></a>另請參閱
[若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)