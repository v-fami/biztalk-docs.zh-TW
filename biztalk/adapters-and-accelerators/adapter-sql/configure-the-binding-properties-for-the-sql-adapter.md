---
title: 設定 SQL 配接器的繫結屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2edbd90-039a-48b4-a6fc-d825b4957207
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42576a59aae28c78250f5eba19558072e0e526d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224702"
---
# <a name="configure-the-binding-properties-for-the-sql-adapter"></a>設定 SQL 配接器的繫結屬性
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]呈現數個繫結屬性可讓您控制其行為特性，部份。 本節提供設定的繫結內容的相關資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]來回[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定要產生結構描述的特定作業的繫結屬性。 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須指定的繫結屬性一部分的傳送或接收埠的傳送或接收訊息，從 SQL Server。  
  
 如需繫結屬性的資訊，包括清單的繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
## <a name="enter-the-binding-properties-in-visual-studio"></a>在 Visual Studio 中輸入的繫結屬性  
 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您可以指定繫結屬性使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
### <a name="using-consume-adapter-service-add-in"></a>使用會耗用配接器服務增益集  
  
1.  以滑鼠右鍵按一下您的 BizTalk 專案，然後選取**新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**取用配接器服務**。|  
    |**範本**|按一下**取用配接器服務**。|  
  
3.  若要啟動**取用配接器服務**對話方塊中，按一下 **新增**。  
  
4.  在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**.  
  
5.  在**設定配接器**對話方塊中，按一下 **繫結屬性**索引標籤，然後再指定不同的繫結屬性。  
  
6.  按一下 **[確定]**。  
  
### <a name="using-add-adapter-metadata-wizard"></a>使用新增配接器中繼資料精靈  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 **新增產生的項目**。  
  
2.  在**新增產生的項目**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**類別**|按一下**新增介面卡**。|  
    |**範本**|按一下**新增配接器中繼資料**。|  
  
3.  按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  
  
4.  在 新增配接器精靈 中，選取  **WCF-SQL**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  
  
    > [!IMPORTANT]
    >  如果您已經在 BizTalk 中設定 WCF SQL 連接埠，選取 從連接埠**連接埠**清單。  
  
5.  按一下 **[下一步]**。  
  
6.  在**取用配接器服務**對話方塊中，從**選取繫結**下拉式清單中選取**sqlBinding**，然後按一下 **設定**.  
  
7.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    > [!NOTE]
    >  如果您選取現有的 WCF SQL 傳送埠時，您不需要指定繫結屬性。 繫結屬性是從傳送埠組態中挑選。 不過，您可以選擇以指定的繫結內容所需在設計階段，如果有的話。 在這種情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段的繫結屬性的傳送埠組態中指定的值將會適用。  
  
8.  按一下 **[確定]**。  
  
## <a name="enter-binding-properties-from-the-biztalk-server-administration-console"></a>從 BizTalk Server 管理主控台中輸入繫結屬性  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以指定的繫結屬性為 Wcf-custom 或 WCF SQL 連接埠組態的一部分。  
  
### <a name="enter-binding-properties-for-wcf-custom-port"></a>輸入 WCF 自訂連接埠繫結屬性  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
3.  在 連接埠屬性 對話方塊中，從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
4.  在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
5.  從**繫結的型別**清單中，選取**sqlBinding**。  
  
6.  在**組態**方塊、 指定不同的繫結屬性的值，然後按一下**確定**。  
  
### <a name="enter-binding-properties-for-the-wcf-sql-port"></a>輸入 WCF SQL 連接埠繫結屬性  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立的連接埠，並按一下**傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  
  
4.  在 [連接埠屬性] 對話方塊中，從**類型**下拉式清單中，選取您稍早，新增 WCF-SQL 配接器，然後按一下**設定**。  
  
    > [!NOTE]
    >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**在左窗格中的連接埠屬性對話方塊、 標籤，然後按一下**新增**。  
  
5.  在 傳輸屬性對話方塊中，按一下 **繫結**索引標籤上，並且指定繫結屬性的值。  
  
    > [!NOTE]
    >  根據您要設定傳送埠或接收埠會繫結屬性。 例如，通知相關的繫結屬性沒有可用時設定的傳送埠，因為通知為輸入的作業，需要接收埠組態。  
  
6.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)