---
title: 檢查清單： 更新組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5afcb78a-333b-46ff-8681-42362ce5aaad
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b20aa7d1b0b901176f090ab7636ef0b3eccfa9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300766"
---
# <a name="checklist-updating-an-assembly"></a>檢查清單： 更新組件
下列檢查清單描述更新一或多個成品的應用程式，已部署，並再重新部署應用程式的程序。  
  
> [!NOTE]  
>  如果您無法排程停機，或有非常長時間執行的執行個體，無法終止該工作，請使用-並存版本控制更新。  
  
|步驟|參考|  
|-----------|---------------|  
|檢視更新應用程式內成品時的重要考量。|-   [更新應用程式的重要考量](http://go.microsoft.com/fwlink/?LinkId=154823)(http://go.microsoft.com/fwlink/?LinkId=154823)。<br />-   [更新應用程式的最佳作法](../technical-guides/best-practices-for-updating-applications.md)|  
|確定您具有適當的權限可執行該部署。|[管理應用程式的權限](../technical-guides/permissions-for-managing-an-application.md)|  
|組件，加入、 移除或重新設定成品，視需要進行任何必要的變更。<br /><br /> 從 Visual Studio 組件到 BizTalk 應用程式在開發環境中部署。|-   [如何更新組件](../technical-guides/how-to-update-an-assembly.md)<br />-   [更新成品](../technical-guides/updating-an-artifact.md)<br />-「 更新成品 」 和 「 更新組件 」 的區段[更新應用程式的最佳作法](../technical-guides/best-practices-for-updating-applications.md)<br />-   [如何部署 BizTalk 組件從 Visual Studio](http://go.microsoft.com/fwlink/?LinkId=154824) (http://go.microsoft.com/fwlink/?LinkId=154824)。|  
|測試任何新成品或已變更的成品，此外也務必測試任何可能相依於新成品或已變更成品的成品。 **注意：** 測試時，務必要考慮可能存在於此應用程式和其他應用程式之間的相依性。|[BizTalk 應用程式部署的測試工作](http://go.microsoft.com/fwlink/?LinkId=154825)(http://go.microsoft.com/fwlink/?LinkId=154825)。|  
|在 BizTalk Server 管理主控台中，加入、 移除或重新設定視應用程式中的成品。|-   [如何建立或新增成品](http://go.microsoft.com/fwlink/?LinkID=154724)(http://go.microsoft.com/fwlink/?LinkID=154724)。<br />-   [如何從應用程式移除成品](http://go.microsoft.com/fwlink/?LinkID=154688)(http://go.microsoft.com/fwlink/?LinkID=154688)。<br />-   [管理成品](http://go.microsoft.com/fwlink/?LinkID=154725)(http://go.microsoft.com/fwlink/?LinkID=154725)。<br />-   [更新成品](../technical-guides/updating-an-artifact.md)<br />-「 更新成品 」 一節[更新應用程式的最佳作法](../technical-guides/best-practices-for-updating-applications.md)。|  
|將包含新成品或已變更成品的應用程式匯出至 .msi 檔案。|-   [匯出 BizTalk 應用程式、 繫結和原則](http://go.microsoft.com/fwlink/?LinkId=154826)(http://go.microsoft.com/fwlink/?LinkId=154826)。<br />-   [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-「 匯出 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](../technical-guides/best-practices-for-deploying-an-application.md)。|  
|如果更新會影響與應用程式執行時，排定停機時間，並停止您想要更新的應用程式。|-   [如何啟動和停止 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154729)(http://go.microsoft.com/fwlink/?LinkID=154729)。<br />-「 啟動或停止應用程式 」 一節[更新應用程式的最佳作法](../technical-guides/best-practices-for-updating-applications.md)。|  
|匯入已變更或更新成品從.msi 檔案到您想要更新，應用程式安裝應用程式。 **注意：** 當您更新 BizTalk 組件時，您應該停止並取消登錄的成品從.msi 檔案匯入之前。 您應該重新登記，並從.msi 匯入後，再啟動 BizTalk 成品。|-   [如何匯入 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkId=154827)(http://go.microsoft.com/fwlink/?LinkId=154827)。<br />-   [如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-「 匯入 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](../technical-guides/best-practices-for-deploying-an-application.md)。<br />-   [如何安裝 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154728)(http://go.microsoft.com/fwlink/?LinkID=154728)。<br />-   [如何在 GAC 中安裝組件](http://go.microsoft.com/fwlink/?LinkId=154828)(http://go.microsoft.com/fwlink/?LinkId=154828)。|  
|啟動應用程式，並繼續訊息發佈。 重新啟動所有 BizTalk 主控件執行個體。|-   [如何啟動和停止 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154729)(http://go.microsoft.com/fwlink/?LinkID=154729)。|  
|在匯入包含協調流程的組件之後，如果您要匯入的目的應用程式已經包含具有相同名稱、公開金鑰 Token 與版本的組件，請停止再啟動協調流程所繫結之主控件的主控件執行個體。 這可以確保 BizTalk Server 會使用新版本的組件。|-   [如何停止主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=154829)(http://go.microsoft.com/fwlink/?LinkId=154829)。<br />-   [如何啟動主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=154830)(http://go.microsoft.com/fwlink/?LinkId=154830)。|