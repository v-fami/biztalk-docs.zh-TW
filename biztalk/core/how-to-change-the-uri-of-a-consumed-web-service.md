---
title: 如何變更已使用的 Web 服務的 URI |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, modifying
- Web services, consuming
- consuming [Web services]
- modifying, Web services
ms.assetid: 907de565-8c99-4d34-939f-fd3dba37dd11
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b9ae7d7178fc24c5f16b28325fb627045e5273a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247398"
---
# <a name="how-to-change-the-uri-of-a-consumed-web-service"></a>如何變更已使用的 Web 服務的 URI
部署協調流程後，BizTalk Server 會為協調流程參考的每個 Web 服務設定傳送埠。 依照預設，BizTalk 在執行階段使用的 Web 服務 URL，和匯入的 Web 服務 URL 相同。 您可以使用 BizTalk Server 管理主控台來變更此 URL。  
  
> [!NOTE]
>  您必須先部署協調流程，才能變更已使用的 Web 服務的 URI。 如需有關如何部署您的協調流程的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
### <a name="to-change-the-uri-of-a-consumed-web-service-using-biztalk-server-administration-console"></a>若要使用 BizTalk Server 管理主控台變更已使用的 Web 服務的 URI  
  
1.  在 BizTalk Server 管理主控台中，展開 BizTalk 應用程式，然後展開**傳送埠**節點。  
  
2.  以滑鼠右鍵按一下 設定與 SOAP 配接器的傳送埠，請按一下**屬性**。  
  
3.  若您沒有實體連接埠，可以使用 [BizTalk 管理主控台] 建立傳送埠和接收位置。 如需資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
4.  在**傳送屬性**對話方塊中，按一下 **設定**。  
  
5.  在**SOAP 傳輸屬性**對話方塊中，於**Web 服務 URL**方塊中，輸入 Web 服務中的位置的完整 URL，然後按一下**確定**。  
  
    > [!NOTE]
    >  請確定您指定的 URL 是否有 Web 服務存在。 BizTalk Server 不會驗證 URL 位置。  
  
6.  按一下 確定 以結束**傳送屬性** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)   
 [如何設定 SOAP 傳送埠](../core/how-to-configure-a-soap-send-port.md)   
 [SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md)   
 [建立 Web 連接埠](../core/creating-web-ports.md)