---
title: 設定 SAP 配接器的繫結屬性 |Microsoft 文件
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
ms.assetid: 259a5895-c19d-409c-b2fc-bfdf59d5d74b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a16a95818ed4d63fd97b9fca1f9ea86ebd14de80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217438"
---
# <a name="configure-the-binding-properties-for-the-sap-adapter"></a>設定 SAP 配接器的繫結屬性
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。 本節提供從 Visual Studio （設計階段），然後從設定的繫結屬性的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台 （執行時間）。 在設計階段，您必須指定要產生結構描述的特定作業的繫結屬性。 在執行階段，必須指定的繫結屬性一部分傳送或接收埠的傳送或接收訊息從 SAP 系統。  
  
 如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
## <a name="enter-binding-properties-at-design-time"></a>在設計階段輸入繫結屬性  
 設計階段，您可以指定繫結屬性使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a>輸入使用配接器服務增益集所使用的繫結屬性  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**取用配接器服務**。|  
    |**範本**|按一下**取用配接器服務**。|  
  
3.  若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。  
  
4.  在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.  
  
5.  在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤，然後再指定不同的繫結屬性。  
  
6.  按一下 **[確定]**。  
  
### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a>輸入繫結屬性使用 新增配接器中繼資料精靈  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**新增介面卡**。|  
    |**範本**|按一下**新增配接器中繼資料**。|  
  
3.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
4.  在 新增配接器精靈 中，選取  **WCF SAP**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  
  
    > [!IMPORTANT]
    >  如果您已經在 BizTalk 中設定 WCF SAP 連接埠，選取 從連接埠**連接埠**清單。  
  
5.  按一下 **[下一步]**。  
  
6.  在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中，選取**sapBinding**，然後按一下**設定**.  
  
7.  按一下**繫結屬性**索引標籤上，並指定繫結值，如果有的話，也就是產生結構描述之前必須指定。 例如，您必須指定的值**GenerateFlatFileCompatibleIDoc**屬性，才能產生從 SAP 系統接收 IDOC 的結構描述。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    > [!NOTE]
    >  如果您選取現有的 WCF SAP 傳送埠時，您不需要指定繫結屬性。 繫結屬性是從傳送埠組態中挑選。 不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。 在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。  
  
8.  按一下 **[確定]**。  
  
## <a name="enter-binding-properties-at-run-time"></a>在執行階段輸入繫結屬性  
 對於執行階段，您可以指定繫結屬性為 WCF 自訂連接埠或中的 WCF SAP 組態的一部分[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
### <a name="enter-binding-properties-for-the-wcf-custom-port"></a>輸入 WCF 自訂連接埠繫結屬性  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在**連接埠內容**對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
4.  在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
5.  從**繫結的型別**下拉式清單中，選取**sapBinding**。  
  
6.  在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。  
  
### <a name="enter-binging-properties-for-the-wcf-sap-port"></a>輸入 WCF SAP 連接埠的繫結屬性  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  加入 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您之前，加入 WCF SAP 配接器，然後按一下**設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
5.  在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。  
  
    > [!NOTE]
    >  根據您要設定傳送埠或接收埠會繫結屬性。 比方說，繫結內容相關的輸入都無法使用作業時設定的傳送埠，因為輸入的操作需要接收埠組態。  
  
6.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[若要建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)