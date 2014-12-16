# FpdmBundle
A Symfony2 bundle to fill pdf document forms

Adapted from FPDM class found in the FPDF examples http://www.fpdf.org



## Example

To adapt the FPDF example, make a controller like this:

    // src/Acme/AppBundle/DefaultController.php
    namespace Acme\DefaultBundle\Controller;
    use Acme\FpdmBundle\Model\FPDM;
    use Symfony\Bundle\FrameworkBundle\Controller\Controller;
    
    class DefaultController extends Controller {
        public function indexAction() {
            $fields = array(
                'name'    => 'John',
                'address' => 'Doe',
                'city'    => 'Springfield',
                'phone'   => '123423423'
            );
            $pdf = new FPDM();
            $pdf->FPDM('template.pdf');
            //$pdf->verbose = true;
            //$pdf->verbose_level = 4;
            $pdf->Load($fields, TRUE); // second parameter: false if field values are in ISO-8859-1, true if UTF-8
            $pdf->Merge();
            $pdf->Output();
        }
    }