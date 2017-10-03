---
title: "檢查清單： 更新應用程式使用的並存版本設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3adee8da-18d4-4b9e-a22e-148b90d18179
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5447743ff9cdc7a109d78c3dac57e0e3345556a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-updating-an-application-using-side-by-side-versioning"></a>檢查清單： 更新應用程式使用的並存版本控制
下列檢查清單描述部署 BizTalk 應用程式將會執行由並行的更新的版本的程序與現有版本。  
  
 並存安裝可讓您以累加方式轉出應用程式升級。 您可以讓安裝使用一部分的商務夥伴一開始，而非所有協力電腦一次。 使用這種方法可讓您繼續執行現有的應用程式服務尚未使用新的版本直到您準備好完全移至新版本的使用者。  
  
 兩個並行的應用程式就必須收到接收位置在兩個不同的訊息。 如此一來，若要執行並行的應用程式您必須要求這些交易夥伴誰應該使用新版的應用程式來將訊息傳送至新接收位置，以便將新的版本會處理。 這些交易夥伴應該使用舊的版本應該傳送到先前的訊息接收位置。  
  
|步驟|參考|  
|-----------|---------------|  
|建立和實作版本控制策略。|「 版本控制 > 一節中[更新應用程式的最佳作法](../technical-guides/best-practices-for-updating-applications.md)。|  
|對您想要部署到應用程式的新版本的專案中的任何必要的變更。|-   [如何建立或新增成品](http://go.microsoft.com/fwlink/?LinkID=154724)(http://go.microsoft.com/fwlink/?LinkID=154724)。<br />-   [管理成品](http://go.microsoft.com/fwlink/?LinkID=154725)(http://go.microsoft.com/fwlink/?LinkID=154725)。<br />-   [繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/?LinkID=154726)(http://go.microsoft.com/fwlink/?LinkID=154726)。<br />-   [將成品新增至應用程式](../technical-guides/adding-artifacts-to-an-application.md)|  
|遞增每個組件的版本號碼。|[如何更新組件](../technical-guides/how-to-update-an-assembly.md)|  
|設定方案 （設定目的地應用程式及啟用安裝到全域組件快取 (GAC)） 中的每個專案的部署屬性。|[如何更新組件](../technical-guides/how-to-update-an-assembly.md)|  
|部署包含已變更的組件，在開發環境中的應用程式的方案。|-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。<br />-   [如何重新部署 BizTalk 組件從 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720)。<br />-   [部署組件](../technical-guides/deploying-an-assembly.md)|  
|建立新接收埠和任何必要的接收位置指定您希望夥伴將訊息傳送至新的 Url。<br /><br /> 視需要建立適當的傳送埠。<br /><br /> 必要時，繫結至新建立新的應用程式接收和傳送連接埠，並測試應用程式的運作。|-   [如何建立接收埠](http://go.microsoft.com/fwlink/?LinkId=154843)(http://go.microsoft.com/fwlink/?LinkId=154843)。<br />-   [如何建立接收位置](http://go.microsoft.com/fwlink/?LinkId=154844)(http://go.microsoft.com/fwlink/?LinkId=154844)。<br />-   [如何建立傳送埠](http://go.microsoft.com/fwlink/?LinkId=154845)(http://go.microsoft.com/fwlink/?LinkId=154845)。<br />-   [如何設定應用程式](http://go.microsoft.com/fwlink/?LinkId=154847)(http://go.microsoft.com/fwlink/?LinkId=154847)。|  
|從開發環境中匯出新的應用程式至.msi 檔案。|-   [如何匯出 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkId=154848)(http://go.microsoft.com/fwlink/?LinkId=154848)。<br />-   [繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/?LinkID=154726)(http://go.microsoft.com/fwlink/?LinkID=154726)。<br />-   [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [如何匯出繫結至繫結檔案](../technical-guides/how-to-export-bindings-to-a-binding-file.md)|  
|應用程式.msi 檔案匯入您的生產環境中的 BizTalk 群組。|-   [如何匯入 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkId=154827)(http://go.microsoft.com/fwlink/?LinkId=154827)。<br />-   [如何安裝 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154728)(http://go.microsoft.com/fwlink/?LinkID=154728)。<br />-   [如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-   [如何從繫結檔案匯入繫結](../technical-guides/how-to-import-bindings-from-a-binding-file.md)|  
|執行應用程式完整啟動。|-   [如何啟動和停止 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154729)(http://go.microsoft.com/fwlink/?LinkID=154729)。<br />-   [BizTalk 應用程式部署的測試工作](http://go.microsoft.com/fwlink/?LinkId=154825)(http://go.microsoft.com/fwlink/?LinkId=154825)。|  
|通知您的夥伴，它們應該開始將訊息傳送至新的 Url。 他們這麼做之後，應用程式便會開始處理指定夥伴的訊息。|-|