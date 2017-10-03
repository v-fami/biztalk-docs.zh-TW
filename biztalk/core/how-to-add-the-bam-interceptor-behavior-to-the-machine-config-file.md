---
title: "如何新增 BAM 攔截器行為至 Machine.config 檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea09925-264f-4976-8e34-f63bad70f886
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abc8845333389c95ea52d440437935d4c4867dc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-the-bam-interceptor-behavior-to-the-machineconfig-file"></a>如何新增 BAM 攔截器行為至 Machine.config 檔
若要在 BAM 中攔截資料，您必須將 BAM 攔截器行為新增至 Microsoft .NET machine.config 檔。 執行這項作業的方法有兩種：  
  
-   手動編輯 machine.config 檔來加入此行為。  
  
-   使用 [服務組態編輯器] 加入此行為。  
  
### <a name="to-manually-edit-the-machineconfig-file"></a>手動編輯 machine.config 檔  
  
1.  編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。 若要這樣做，請按一下**啟動**，按一下 **執行**，輸入 c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config，，然後按一下**確定**。  
  
2.  使用下列行為延伸模組更新 machine.config 檔。  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="BAMEndPointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
3.  關閉並儲存 machine.config 檔案。  
  
#### <a name="to-edit-the-machineconfig-file-using-the-service-configuration-editor"></a>使用服務組態編輯器編輯 machine.config 檔  
  
1.  開啟 [服務組態編輯器]。 使用 服務組態編輯器的相關資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557)。  
  
2.  在樹狀檢視窗格中 (標示為**組態**)，展開節點樹狀目錄。 按一下**進階**資料夾中，按一下 **延伸**資料夾，然後再選取**行為項目延伸**項目。  
  
3.  建立新的行為項目延伸模組。 按一下**新增**按鈕以開啟 [延伸模組組態項目編輯器] 對話方塊。 在**組態名稱**輸入行為，例如 BAMEndPointBehaviorExtension 的唯一名稱。  
  
     ![延伸模組組態元素編輯器](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")  
  
4.  按一下**類型**欄位，，然後按一下省略符號按鈕 (**...**) 按鈕來開啟 [行為延伸型別瀏覽器] 對話方塊。  
  
5.  按一下 [全域組件快取] (GAC) 圖示，列出 GAC 中的 DLL。  
  
6.  選取 [Microsoft.BizTalk.Bam.Interceptors] 組件。  
  
7.  按一下**開啟**按紐選取組件，並關閉對話方塊。  
  
     ![Bejavopr 延伸模組型別瀏覽器](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")  
  
8.  在 [行為延伸模組型別瀏覽器] 對話方塊的 [型別名稱] 窗格中，按兩下 [Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior] 型別 (如下方畫面中反白顯示者)。  
  
     ![Bejavopr 延伸模組型別瀏覽器](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")  
  
     這樣做會開啟 [延伸模組組態項目編輯器]。  
  
9. 按一下**確定**關閉延伸模組組態項目編輯器對話方塊。  
  
10. 在 [服務組態編輯器] 的詳細資訊窗格中，確認顯示 BAMEndPointBehaviorExtension。  
  
11. 關閉 [服務組態編輯器]。  
  
## <a name="next-steps"></a>後續步驟  
 [如何設定 BAM WCF 攔截](../core/how-to-configure-the-bam-wcf-interception.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定 WCF 配接器攔截 BAM 資料](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)