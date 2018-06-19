---
title: 步驟 9： 建置並部署回應配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ead10ab-1acf-47c5-ad16-dc6938601906
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b9a4985629427e44b8ca85f324c89ab719cf249
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967236"
---
# <a name="step-9-build-and-deploy-the-echo-adapter"></a>步驟 9： 建置並部署回應配接器
![步驟 9 / 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 **若要完成的時間：** 10 分鐘  
  
 在此步驟中，您將會執行部署回應配接器所需的工作。 這項作業包括下列各項：  
  
-   建立強式名稱的檔案，並將它指派給回應配接器組件  
  
-   建立回應的配接器  
  
-   發行至 GAC 的組件  
  
-   註冊以回應配接器[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 若要成功完成此步驟中，您應該熟悉強式名稱的檔案和 GAC。 基本的了解[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]組態會有所助益，但非必要。  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>指派強式名稱給組件  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**EchoAdapter**專案，然後再按一下**屬性**。  
  
2.  在 [EchoAdapter 屬性頁] 對話方塊中，選取**簽署**從左窗格。  
  
3.  按一下**簽署組件** 索引標籤。  
  
4.  選擇**\<新...\>** 強式名稱的檔案。 出現提示時輸入檔案名稱，輸入**EchoAdapter.snk**，取消選取保護我的金鑰檔使用的密碼選項，然後按一下 **確定**。  
  
5.  按一下**應用程式** 索引標籤。  
  
6.  將組件名稱變更為**Microsoft.Adapters.Samples.EchoV2**。  
  
7.  按一下**檔案**Visual Studio 功能表上選擇 **全部儲存**。  
  
### <a name="to-build-and-deploy-echo-adapter"></a>若要建置和部署回應配接器  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**EchoAdapter**專案，然後再按一下**建置**。 如果組建沒有成功，修正任何錯誤，然後再次嘗試重建回應配接器。  
  
2.  開啟 Visual Studio 命令提示字元。  
  
3.  輸入以下命令：  
  
     **gacutil.exe /if"\<**  *路徑 assembly\Microsoft.Adapters.Samples.EchoV2.dll*  **\>"**  
  
     這會將組件安裝至 GAC，覆寫任何同名的現有組件。  
  
### <a name="to-register-the-echo-adapter-with-windows-communication-foundation"></a>Windows Communication foundation 註冊回應配接器  
  
1.  編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。 若要這樣做，請按一下**啟動**，按一下 **執行**，型別**記事本\<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\machine.config**，然後按一下 **確定**。  
  
2.  更新 machine.config 檔案。 如果 machine.config 未包含的 system.serviceModel 區段，結尾的組態檔，但在結尾根標記之前加入下列區段。  
  
    > [!NOTE]
    >  配接器的資訊來取代版本、 文化特性、 公開金鑰語彙基元和其他組件特定的資訊。  
  
    ```  
    <system.serviceModel>  
      <client>  
        <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
          name="echov2" />  
      </client>  
      <extensions>  
        <bindingElementExtensions>  
          <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingElementExtensions>  
        <bindingExtensions>  
          <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
     - 或 -  
  
     如果 machine.config 包含 system.serviceModel 區段，判斷遺失哪些項目，並將其新增。  
  
    > [!NOTE]
    >  配接器的資訊來取代版本、 文化特性、 公開金鑰語彙基元和其他組件特定的資訊。  
  
    ```  
    <client>  
      <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
        name="echov2" />  
    </client>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingElementExtensions>  
      <bindingExtensions>  
        <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingExtensions>  
    </extensions>  
    ```  
  
3.  儲存 machine.config 檔。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 在此回應配接器教學課程的最後一個步驟中，您加入回應配接器的強式名稱、 建置和部署配接器，然後修改 Machine.config 包含配接器的相關資訊。 此時，回應配接器應該可供取用應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 完成本教學課程。 如果您想要測試的.NET 專案中回應配接器功能，請參閱[教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)。  
  
## <a name="see-also"></a>請參閱  
 [步驟 8： 為回應配接器實作的同步輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)   
 [教學課程 2：從 .NET 使用 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)