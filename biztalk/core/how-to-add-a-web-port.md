---
title: 如何新增 Web 連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web ports, creating
- creating, Web ports
ms.assetid: da94d98e-10ca-437a-ba34-7aa6efc68f3d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42e9853755788aa29d3ca7506829dcd6bdfed53d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248006"
---
# <a name="how-to-add-a-web-port"></a>如何新增 Web 連接埠
您可以使用 [協調流程設計師]，在連接埠介面上新增 Web 連接埠。 不同於其他已設定的連接埠，Web 連接埠支援混合要求 (單向) 和要求-回應 (雙向) 的作業。 Web 連接埠中的每個作業都代表一個 Web 方法。 如果 Web 方法包含*輸入*和*輸出*參數，BizTalk 會建立要求/回應作業。 如果 Web 服務僅包含*輸入*參數，BizTalk 只會建立單向作業。  
  
### <a name="to-add-a-web-port"></a>若要新增 Web 連接埠  
  
1.  在協調流程設計師中，開啟，協調流程連接埠介面，以滑鼠右鍵按一下，然後選取**新設定連接埠**。  
  
2.  在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。  
  
3.  在**連接埠內容**頁面上，於**名稱** 文字方塊中，輸入連接埠的名稱，然後按一下**下一步**。  
  
4.  在**選取連接埠類型**頁面上，選取**使用現有的連接埠類型**。  
  
5.  在**可用的連接埠類型**方塊中，展開  **Web 連接埠類型**節點，然後選取 Web 連接埠來新增 Web 服務中，對應的類型，然後按一下 **下一步**。  
  
     下圖顯示**選取連接埠類型** 對話方塊。  
  
     ![](../core/media/ebiz-prog-ws-addwebport.gif "ebiz_prog_ws_addwebport")  
  
6.  在**連接埠繫結**頁面上，於**連接埠繫結**下拉式清單方塊中，選取**現在指定**。 BizTalk 就會自動將參考的 Web 服務提供的值，放在 URI、傳輸，以及接收和傳送管線中。 當您部署 BizTalk 專案時，BizTalk 會使用這些值來建立傳送埠。  
  
    > [!IMPORTANT]
    >  傳送埠的預設驗證方法是匿名存取。 如果 Web 服務需要不同的驗證或加密方法，您必須變更組態，提供適當的使用者認證或安全通訊端層 (SSL) 以執行 Web 服務。 如需詳細資訊，請參閱[SOAP 傳送配接器](../core/soap-send-adapter.md)和[範例 TMA: HTTP 和 SOAP 配接器](../core/sample-tma-http-and-soap-adapters.md)。  
  
7.  按一下**下一步**，然後**完成**以完成精靈。  
  
## <a name="see-also"></a>另請參閱  
 [如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)   
 [建立 Web 連接埠](../core/creating-web-ports.md)