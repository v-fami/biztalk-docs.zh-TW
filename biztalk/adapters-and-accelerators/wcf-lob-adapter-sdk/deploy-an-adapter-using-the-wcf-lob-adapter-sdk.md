---
title: 部署配接器使用 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 376b4dcf-2d2c-4872-a394-67edc0c3d088
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c29400aae9a9bcd0cf36d49f9b619dc7642fa5a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978471"
---
# <a name="deploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a>部署配接器使用 WCF LOB 配接器 SDK
若要部署配接器，必須將配接器組件安裝到全域組件快取 (GAC)，並再註冊在 machine.config 檔案中的 配接器。  
  
## <a name="install-the-adapter-assembly-into-the-gac"></a>配接器組件安裝到 GAC  
 之前使用在 Visual Studio 中使用配接器[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]命令或在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]功能，您必須將組件安裝到 GAC。 只有為強式名稱的組件可以安裝到 GAC。  
  
> [!NOTE]
>  若要完成此程序，您必須在 GAC 中具有寫入權限的帳戶登入。 本機電腦上的「系統管理員」帳戶具有這些權限。  
  
#### <a name="configure-a-strong-name-assembly-key-file"></a>設定強式名稱組件金鑰檔案  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，載入需要強式名稱的配接器專案檔案。  
  
2. 開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。  
  
3. 在命令提示字元中，切換到您想要儲存金鑰檔案的資料夾，再輸入下列命令，然後按下 ENTER：  
  
    **sn /k***file_name* **.snk**   
  
    範例： **sn /k EchoAdapter.snk**  
  
    確認訊息，**金鑰組寫入** \< *file_name*\>**.snk** `,`會出現在命令列。  
  
4. 在 Visual Studio 方案總管 中，以滑鼠右鍵按一下專案，然後**屬性**。  
  
5. 在左窗格中，依序展開**通用屬性**，然後按一下**組件**。  
  
6. 在右窗格中，捲動到 [**強式名稱**] 方塊中。  
  
7. 在 **強式名稱**方塊中，按一下欄位旁**組件金鑰檔案**，按一下 瀏覽按鈕 (**...**)，然後瀏覽至金鑰檔。  
  
8. 按一下金鑰檔案，請按一下**開放**，然後按一下**確定**。  
  
9. 在 Visual Studio 功能表中，按一下**建置**，然後選擇**建置方案**。  
  
> [!NOTE]
>  如果您的配接器組件相依於任何其他組件，就必須確保這些參考的組件已簽署為強式名稱;否則，您會收到錯誤。  
  
 如果您有來源時，您可以使用強式名稱重新編譯先前所示。 如果參考組件屬於第三方，而且您將無法確定它將會提供強式名稱，您可以解譯，並再重新組合以強式名稱組件。  
  
 您的原始組件將會覆寫，因此如果您想要保留原始的版本，請確定您建立備份複本再繼續進行下列步驟。  
  
 您可以使用 Microsoft Intermediate Language (MSIL) 解譯器來反組譯的組件：  
  
- ILDASM thirdparty.dll /out:thirdparty.il  
  
  您可以使用 MSIL 組譯工具來重組以強式名稱組件：  
  
- ILASM thirdparty.il /dll /key=strongkeyfile.snk  
  
#### <a name="install-an-assembly-in-the-gac"></a>將組件安裝在 GAC 中  
  
1. 請確認您的配接器已經過簽署。  
  
2. 開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。  
  
3. 輸入以下命令：  
  
    **gacutil.exe /if 」\<**  *組件.dll 檔案路徑*  **\>"**  
  
4. 這會將組件安裝至 GAC，覆寫任何同名的現有組件。  
  
## <a name="register-the-adapter-in-machineconfig"></a>在 Machine.config 中註冊配接器  
 使用配接器開發[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會呈現為 WCF 繫結。  如需詳細資訊，請參閱 Microsoft.ServiceModel.Channels.Common.AdapterBinding。  註冊 WCF 配接器繫結使用\<bindingExtensions\>區段內\<系統。ServiceModel\>和 WCF 已註冊的配接器傳輸繫結項目使用\<bindingElementExtensions\>區段內\<系統。ServiceModel\>。  
  
 您可以手動編輯 machine.config 檔，使用文字編輯器。  
  
#### <a name="manually-edit-the-machineconfig-file"></a>手動編輯 machine.config 檔  
  
1. 編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。 若要這樣做，請按一下**開始**，按一下**執行**，輸入 notepad \<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\在 machine.config 中，然後再按一下**確定**。  
  
2. 更新 machine.config 檔案。 如果檔案不包含 system.serviceModel 區段，結尾的組態檔，但在關閉根標記之前新增下一節。  
  
   > [!NOTE]
   >  取代您的配接器資訊的 「 myAdapterBinding"、 版本、 文化特性和其他組件特定的資訊。  
  
   ```  
   <system.serviceModel>  
     <extensions>  
       <bindingExtensions>  
           <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
       </bindingExtensions>      <bindingElementExtensions>  
           <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
         </bindingElementExtensions>  
     </extensions>  
   </system.serviceModel>  
   ```  
  
   - 或 -  
  
     如果 machine.config 檔案中包含的 system.serviceModel 區段，判斷哪些項目遺漏，以及加入它們，以您的配接器資訊取代"MyAdapter 」 和其他資訊。  
  
   ```  
   <extensions>  
     <bindingExtensions>  
           <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
     </bindingExtensions>  
         <bindingElementExtensions>  
           <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
         </bindingElementExtensions>  
   </extensions>  
   ```  
  
3. 關閉並儲存 machine.config 檔案。  
  
   您也可以使用[服務組態編輯器](https://msdn.microsoft.com/library/ms732009.aspx)修改 machine.config 檔案。
  
#### <a name="edit-the-machineconfig-file-using-the-service-configuration-editor"></a>編輯 machine.config 檔，使用 服務組態編輯器  
  
1.  開啟**服務組態編輯器**。 請參閱[服務組態編輯器](https://msdn.microsoft.com/library/ms732009.aspx)如需詳細資訊。
  
2.  在樹狀檢視窗格中 (標示**組態**)，展開節點樹狀結構。 按一下 **進階**資料夾中，按一下**延伸模組**資料夾，然後再選取繫結延伸模組項目。  
  
     ![服務組態編輯器。](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0a44a070-b788-4287-bd9e-c946fafcf11c.gif "0a44a070-b788-4287-bd9e-c946fafcf11c")  
  
3.  建立新的繫結延伸模組。 按一下 [**的新**按鈕以開啟延伸模組**組態項目編輯器**] 對話方塊。 在 **組態名稱**，輸入唯一的名稱，擴充功能，例如*MyAdapterExtension*。  
  
     ![延伸模組組態元素編輯器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/1398a256-00fa-4591-99ee-54298a8cf6e3.gif "1398a256-00fa-4591-99ee-54298a8cf6e3")  
  
4.  按一下 **型別**欄位，，然後按一下 省略符號按鈕 (**...**) 以開啟**繫結延伸模組類型瀏覽器** 對話方塊。  
  
5.  按一下全域組件快取 (GAC) 圖示，列出 GAC 中的 Dll。  
  
6.  按一下您的配接器組件。  
  
     ![建置延伸模組類型瀏覽器。](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7528e218-8930-4b01-b29d-8ec125a9b818.gif "7528e218-8930-4b01-b29d-8ec125a9b818")  
  
7.  按一下 **開啟**按鈕以選取的組件。  
  
8.  在 **繫結延伸模組類型瀏覽器**對話方塊方塊中，按一下 實作繫結集合項目型別名稱。  
  
     ![建置延伸模組類型瀏覽器。](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce.gif "a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce")  
  
9. 按一下 **開啟**按鈕以選取的類型。  
  
10. 按一下 [ **[確定]** 以關閉**延伸模組組態元素編輯器**] 對話方塊。  
  
11. 在詳細資料窗格中的**繫結延伸模組編輯器**，確認您的繫結延伸模組會出現。 在下圖中，MyAdapterExtension 會反白顯示。  
  
     ![具有新增延伸模組的服務組態編輯器。](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")  
  
12. 關閉**服務組態編輯器**。  
  
## <a name="see-also"></a>另請參閱  
 [部署配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)