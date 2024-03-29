---
title: 使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 041f14cc-d00f-450d-b1e9-40a3e423c510
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b75a3fb19f10188c91120ec816e59996e18c644
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998263"
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-biztalk-server-project"></a>使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案
本主題描述如何使用配接器使用來建置[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  

> [!NOTE]
>  若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您必須安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]工具在相同的電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  


## <a name="use-the-consume-adapter-service-add-in"></a>使用取用配接器服務增益集  


1. 開啟您的.NET 應用程式中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

2. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在**專案**窗格中，以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，，然後選擇**新增**&#124;**新增產生的項目** &#124; **使用配接器服務**。  

3. 在 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]畫面上，選取的配接器繫結。  

4. 按一下 **設定**設定選取的配接器繫結的連接 URI，並提供任何認證、 URI 屬性和繫結屬性。 實際需求會依選取的配接器繫結。  

5. 按一下 **確定**當您已設定的 URI。  

6. 按一下 **[連接]**。 連線 URI 是否有效，且接受用戶端認證 （如果有的話），則**分類**窗格應該填入的類別和配接器所提供的作業。  

7. 如果配接器支援搜尋，則可使用 [搜尋] 欄位。 否則您可以在 依合約類型篩選，並探索類型和作業中的節點，即可**分類**窗格。  

8. 按一下 **確定**產生 proxy 成品。 成品數目會根據合約類型而不同：  


   | 合約型別 |  成品   |                         描述                         |                                                             |
   |---------------|-------------|-------------------------------------------------------------|-------------------------------------------------------------|
   |   輸出    | XML 結構描述 | 包含所選的類型和作業的結構描述。 |                                                             |
   |   輸出    |             |        WCF 自訂傳送連接埠繫結資訊的 XML         |  包含針對 Wcf-custom 傳送埠的組態 XML。   |
   |    輸入    | XML 結構描述 | 包含所選的類型和作業的結構描述。 |                                                             |
   |    輸入    |             |       WCF 自訂接收 XML 的連接埠繫結資訊       | WCF 自訂接收埠，請包含組態 XML。 |


9. 您現在可以使用 XML 結構描述檔案，在您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式。  

## <a name="deploy-the-biztalk-server-project"></a>部署 BizTalk Server 專案  

1. 開啟 [BizTalk Server 管理] 。  

2. 匯入所要建立實體連接埠的連接埠繫結 XML 檔案。 以滑鼠右鍵按一下待測應用程式**應用程式**群組中，選取**匯入繫結**，然後瀏覽至並選取適當的連接埠繫結資訊 XML 檔案。  

3. 對應中所定義的邏輯連接埠您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]至新建立的實體連接埠的協調流程。  

4. 按一下 **協調流程**您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下**登錄**。  

5. 按一下 **協調流程**您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下**開始**。  

6. 以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，，然後按一下**啟動**。  

## <a name="generate-multiple-schemas"></a>產生多個結構描述  
 如果您使用 取用配接器服務精靈來產生多個結構描述時，一或多個項目可能會導致編譯失敗的結構描述中重複[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。 您可以選取來避免這**產生唯一的結構描述型別**核取方塊，以確保結構描述型別會產生具有唯一的命名空間。  

## <a name="see-also"></a>另請參閱  
 [使用配接器使用 WCF LOB 配接器 SDK 所建立](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)