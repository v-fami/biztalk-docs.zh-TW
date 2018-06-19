---
title: 檢查清單： 部署應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e699ac3-7998-48d6-96b7-2f8f1a3d52e5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 713eef12a06cb8331faf39acede7c14143a45032
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299854"
---
# <a name="checklist-deploying-an-application"></a>檢查清單： 部署應用程式
本主題說明部署 BizTalk 應用程式和其在生產環境中的成品所需的步驟。 它會示範如何部署開發環境中的應用程式，將它匯出至.msi 檔案，然後將它匯入到生產環境，從.msi 檔案。  
  
 應用程式部署是由應用程式匯入的群組和群組中的個別伺服器 （主控件執行個體） 上安裝應用程式所組成。 如需有關匯入和安裝應用程式的詳細資訊，請參閱[如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)。  
  
 如需應用程式部署的詳細資訊，請參閱[應用程式部署程序](http://go.microsoft.com/fwlink/p/?LinkId=154716)(http://go.microsoft.com/fwlink/p/?LinkId=154716)。  
  
|步驟|參考|  
|-----------|---------------|  
|確定您有適當的權限來執行部署。|[管理應用程式的權限](../technical-guides/permissions-for-managing-an-application.md)|  
|Visual Studio 中設定部署屬性，BizTalk Server 解決方案，包括組件將會部署到應用程式中每個專案。<br /><br /> 部署 （或重新部署） 到開發環境中的 BizTalk 應用程式所需的 BizTalk Server 組件。|-   [如何在 Visual Studio 中設定部署屬性](http://go.microsoft.com/fwlink/p/?LinkId=154718)(http://go.microsoft.com/fwlink/p/?LinkId=154718)。<br />-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=154719)(http://go.microsoft.com/fwlink/p/?LinkId=154719)。<br />-   [如何重新部署 BizTalk 組件從 Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=154720) (http://go.microsoft.com/fwlink/p/?LinkId=154720)。<br />-   [部署組件](../technical-guides/deploying-an-assembly.md)<br />-部署 BizTalk 應用程式 」、 「 建立 BizTalk 應用程式 」 和部署 BizTalk 組件 」 的區段[部署應用程式的最佳作法](http://msdn.microsoft.com/library/gg634504.aspx)。<br />-部署 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)。|  
|將成品新增到 BizTalk 應用程式，並在開發環境中設定成品。<br /><br /> 這可能包括分解成多個 BizTalk 應用程式的成品。|-   [如何建立或新增成品](http://go.microsoft.com/fwlink/p/?LinkId=154724)(http://go.microsoft.com/fwlink/p/?LinkId=154724)。<br />-   [管理成品](http://go.microsoft.com/fwlink/p/?LinkId=154725)(http://go.microsoft.com/fwlink/p/?LinkId=154725)。<br />-   [繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/p/?LinkId=154726)(http://go.microsoft.com/fwlink/p/?LinkId=154726)。<br />-   [將成品新增至應用程式](../technical-guides/adding-artifacts-to-an-application.md)<br />-「 將成品新增至 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](http://msdn.microsoft.com/library/gg634504.aspx)。<br />-「 將成品新增至 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)。|  
|匯出至.msi 檔案，在開發環境中的 BizTalk 應用程式。|-   [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-「 匯出 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](http://msdn.microsoft.com/library/gg634504.aspx)。<br />-「 匯出 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)。|  
|實際執行環境，從.msi 檔案匯入 BizTalk 應用程式。 （這項作業包括的應用程式匯入群組，如果應用程式包含以檔案為基礎的成品，請在群組中每部伺服器上安裝應用程式）。|-   [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [如何安裝應用程式](http://go.microsoft.com/fwlink/p/?LinkId=154728)(http://go.microsoft.com/fwlink/p/?LinkId=154728)。<br />-「 匯入 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](http://msdn.microsoft.com/library/gg634504.aspx)<br />-「 匯入 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)|  
|因此它會在該環境，例如變更連接埠組態中執行，請在生產環境中進行任何其他的修改 BizTalk 應用程式。 如果您這樣做，請匯出至.msi 檔案的應用程式。|-   [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [建立和修改 BizTalk 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=154727)(http://go.microsoft.com/fwlink/p/?LinkId=154727)。<br />-   [如何將繫結檔案新增至 Application1](../technical-guides/how-to-add-a-binding-file-to-an-application1.md)<br />-「 匯出 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](http://msdn.microsoft.com/library/gg634504.aspx)<br />-「 匯出 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)|  
|如果您進行了任何其他修改 BizTalk 應用程式在生產環境中安裝 BizTalk 應用程式從.msi 檔案匯入任何其他電腦將執行它在生產環境中。<br /><br /> 此外，將應用程式匯入您要部署它，任何其他 BizTalk 群組，而且如果應用程式包含以檔案為基礎的成品，則在這些群組中的伺服器上安裝應用程式。|-   [如何安裝 BizTalk 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=154728)(http://go.microsoft.com/fwlink/p/?LinkId=154728)。<br />-   [如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-「 匯入 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](http://msdn.microsoft.com/library/gg634504.aspx)<br />-「 匯入 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)|  
|在實際執行環境，從 BizTalk Server 管理主控台中啟動 BizTalk 應用程式，並確認正常。|-   [如何啟動和停止 BizTalk 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=154729)(http://go.microsoft.com/fwlink/p/?LinkId=154729)。<br />-   [測試應用程式](../technical-guides/testing-an-application.md)|  
  
## <a name="see-also"></a>另請參閱  
 [部署組件](../technical-guides/deploying-an-assembly.md)   
 [將成品新增至應用程式](../technical-guides/adding-artifacts-to-an-application.md)   
 [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)   
 [如何匯出繫結至繫結檔案](../technical-guides/how-to-export-bindings-to-a-binding-file.md)   
 [如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)   
 [如何安裝應用程式](../technical-guides/how-to-install-an-application.md)   
 [如何從繫結檔案匯入繫結](../technical-guides/how-to-import-bindings-from-a-binding-file.md)