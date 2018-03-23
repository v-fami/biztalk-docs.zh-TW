---
title: 使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 041f14cc-d00f-450d-b1e9-40a3e423c510
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84f81d23b56c2631879f366e6fe502840408a0d7
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-biztalk-server-project"></a>使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案
本主題描述如何使用配接器使用建置[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
> [!NOTE]
>  若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您必須安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]上相同的電腦裝載的工具[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 
## <a name="use-the-consume-adapter-service-add-in"></a>使用使用配接器服務增益集  
 
  
1.  開啟.NET 應用程式中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在**專案** 窗格中，以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，然後再選擇**新增**&#124;**新增產生的項目** &#124; **使用配接器服務**。  
  
3.  在[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]畫面上，選取配接器繫結。  
  
4.  按一下**設定**設定選取的配接器繫結的連線 URI，並提供任何認證、 URI 屬性和繫結屬性。 實際需求依選取的配接器繫結上。  
  
5.  按一下**確定**URI 的設定時。  
  
6.  按一下 **[連接]**。 連線 URI 是否有效且用戶端認證 （如果有的話） 已被接受，**類別**窗格應填入的類別和配接器所提供的作業。  
  
7.  如果配接器支援搜尋，[搜尋] 欄位將會啟用。 否則，您可以依合約類型和篩選中的節點，即可瀏覽型別和作業**類別**窗格。  
  
8.  按一下**確定**產生 proxy 成品。 成品數目會根據合約型別而異：  
  
    |合約型別|成品|Description||  
    |-------------------|--------------|-----------------|-|  
    |輸出|XML 結構描述|包含所選的類型和作業的結構描述。||  
    |輸出||WCF 自訂傳送連接埠繫結資訊的 XML|包含 Wcf-custom 傳送埠組態 XML。|  
    |輸入|XML 結構描述|包含所選的類型和作業的結構描述。||  
    |輸入||WCF 自訂接收連接埠繫結資訊的 XML|WCF 自訂接收埠，請包含組態 XML。|  
  
9. 您現在可以使用 XML 結構描述檔案，在您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式。  
  
## <a name="deploy-the-biztalk-server-project"></a>部署 BizTalk Server 專案  
  
1.  開啟 [BizTalk Server 管理] 。  
  
2.  匯入所要建立實體連接埠的連接埠繫結 XML 檔案。 以滑鼠右鍵按一下待測應用程式**應用程式**群組中，選取**匯入繫結**，然後瀏覽至並選取適當的連接埠繫結資訊 XML 檔案。  
  
3.  對應中所定義的邏輯連接埠您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]至新建立的實體連接埠的協調流程。  
  
4.  按一下**協調流程**下您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下 **登錄**。  
  
5.  按一下**協調流程**下您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下 **啟動**。  
  
6.  以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，，然後按一下**啟動**。  
  
## <a name="generate-multiple-schemas"></a>產生多個結構描述  
 如果您使用 取用配接器服務精靈產生多個結構描述時，一或多個項目可能會導致編譯錯誤的結構描述中重複[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。 您可以避免這個狀況選取**產生唯一的結構描述型別**核取方塊，以確保與唯一的命名空間會產生結構描述型別。  
  
## <a name="see-also"></a>另請參閱  
 [使用建立使用 WCF LOB Adapter SDK 的配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)