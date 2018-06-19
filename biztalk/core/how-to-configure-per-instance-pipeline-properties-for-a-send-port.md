---
title: 如何設定傳送埠的每個執行個體管線屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- managing [pipelines], properties
- configuring, send ports
- configuring, pipelines
- managing [pipelines], configuring
- managing [send ports], pipelines
- managing [send ports], configuring
- send ports, pipelines
- pipelines, configuring
ms.assetid: c58faa9e-0dfb-458b-8f1b-d3c91bce0436
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfb9927dca890a7f84baf372c4fa250a8ced17c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249262"
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-send-port"></a>如何設定傳送埠的個別執行個體管線屬性
本主題描述如何在將管線部署到 BizTalk 群組後，使用 BizTalk Server 管理主控台來設定傳送埠的管線屬性。 您所做的變更只會覆寫這個傳送埠的預設管線屬性，因此您也可以為 BizTalk 群組中的每個傳送埠設定不同的管線屬性。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
> [!NOTE]
>  當您使用每個執行個體管線屬性設定的值時**DocumentSpecNames** XML 解譯器元件的管線、 指定的文件結構描述和管線中的屬性必須定義相同專案中。  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-send-port"></a>設定傳送埠的個別執行個體管線屬性  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含您要設定管線屬性中，展開 傳送埠的 BizTalk 群組**應用程式**，然後按一下展開包含該傳送埠的應用程式。  
  
3.  按一下**傳送埠**資料夾中，以滑鼠右鍵按一下傳送埠，然後**屬性**。  
  
4.  按一下省略符號 (**...**) 右邊的按鈕**傳送管線**方塊。  
  
5.  設定的屬性，然後按**確定**。 按一下**協助**如需詳細資訊的屬性頁面上。  
  
    > [!IMPORTANT]
    >  請確定您已輸入管線屬性的正確資訊。 如果輸入無效的值 (例如，輸入字串而非數字)，將會產生錯誤。  
  
6.  如果這是請求-回應傳送埠，按一下省略符號 (**...**) 右邊的按鈕**接收管線**方塊。  
  
7.  設定的屬性，然後按**確定**兩次。 按一下**協助**如需詳細資訊的屬性頁面上。  
  
## <a name="see-also"></a>另請參閱  
 [管理管線](../core/managing-pipelines.md)   
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)   
 [管理接收位置](../core/managing-receive-locations.md)