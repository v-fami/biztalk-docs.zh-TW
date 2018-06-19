---
title: 設定 siebel 繫結屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at design time
- binding properties, specifying at run time
- how to, specify binding properties at design time
- how to, specify binding properties at run time
ms.assetid: 063e9507-8172-4fb0-8b9f-2f95e8a82f21
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b26e9e89319a14317113b730adb189f2f17587f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223134"
---
# <a name="configure-the-binding-properties-for-siebel"></a>設定 siebel 繫結屬性
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。 本節提供從 Visual Studio （設計階段），然後從設定的繫結屬性的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 （執行時間）。 在設計階段，您必須指定要產生結構描述的特定作業的繫結屬性。 在執行階段，您必須指定的繫結屬性的傳送埠將訊息傳送至 Siebel 系統的一部分。  
  
 如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
## <a name="enter-the-binding-properties-at-design-time"></a>在設計階段輸入的繫結屬性  
 設計階段，您必須指定的繫結內容[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] 對話方塊。  
  
#### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a>輸入使用配接器服務增益集所使用的繫結屬性  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**取用配接器服務**。|  
    |**範本**|按一下**取用配接器服務**。|  
  
3.  若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。  
  
4.  在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**.  
  
5.  在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
6.  按一下 **[確定]**。  
  
#### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a>輸入繫結屬性使用 新增配接器中繼資料精靈  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**新增介面卡**。|  
    |**範本**|按一下**新增配接器中繼資料**。|  
  
3.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
4.  在 新增配接器精靈 中，選取  **Wcf-siebel**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  
  
    > [!IMPORTANT]
    >  如果您已設定在 BizTalk Wcf-siebel 連接埠，選取從連接埠**連接埠**清單。  
  
5.  按一下 **[下一步]**。  
  
6.  在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**siebelBinding**，然後按一下**設定**.  
  
7.  在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
    > [!NOTE]
    >  如果您選取現有的 WCF Siebel 傳送埠時，您不需要指定繫結屬性。 繫結屬性是從傳送埠組態中挑選。 不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。 在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。  
  
8.  按一下 **[確定]**。  
  
## <a name="enter-binding-properties-at-run-time"></a>在執行階段輸入繫結屬性  
 執行階段，您必須指定的繫結屬性，Wcf-custom 或 Wcf-siebel 連接埠組態中的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
#### <a name="enter-binding-properties-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠繫結屬性  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下**傳送埠**. 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在**連接埠內容**對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
4.  在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
5.  從**繫結的型別**下拉式清單中，選取**siebelBinding**。  
  
6.  在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。  
  
#### <a name="enter-binding-properties-for-the-wcf-siebel-port"></a>輸入 Wcf-siebel 連接埠繫結屬性  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下**傳送埠**. 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在**連接埠內容**對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 Wcf-siebel 連接埠，然後按一下**設定**。  
  
5.  在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，指定繫結屬性的值。  
  
6.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)